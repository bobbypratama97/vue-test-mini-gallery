<template>
  <div id="index">
    <h1>Mini Gallery Kompas</h1>
    <div class="formInput">
      <div>
        <input type="text" v-model="title" style="margin-bottom:5px" placeholder="Title" />
      </div>
      <div>
        <input
          type="text"
          v-model="description"
          style="margin-bottom:5px"
          placeholder="Description"
        />
      </div>
      <div>
        <input type="text" v-model="url" style="margin-bottom:5px" placeholder="Url" />
      </div>

      <button @click="add()">Insert</button>
    </div>

    <div class="mainGallery">
      <div class="carousel-view">
        <transition-group class="carousel" tag="div">
          <div v-for="g in gallery" class="gallery" :key="g.id">
            <div>
              <img v-bind:src="g.url" alt width="800" height="600" />
              <div>
                <h4>{{g.description}}</h4>
              </div>
            </div>
          </div>
        </transition-group>
        <div class="carousel-controls">
          <button class="carousel-controls__button" @click="previous">prev</button>
          <button class="carousel-controls__button" @click="next">next</button>
        </div>
      </div>
    </div>
    <div
      v-for="g in gallery"
      :key="g.id"
      class="image"
      @click="showImage(g.id,g.url,g.description)"
      :style="{backgroundImage: 'url(' + g.url + ')', width: '300px', height: '200px',textAlign:'center'}"
    ></div>
    <!-- </div> -->
  </div>
</template>

<script>
export default {
  name: "Index",
  data: function() {
    return {
      id: 0,
      title: "",
      description: "",
      url: "",
      gallery: [],
      show: false,
      temp: [],
      index: null
    };
  },
  methods: {
    add: function() {
      var obj = {
        id: this.id++,
        title: this.title,
        description: this.description,
        url: this.url
      };
      this.gallery.push(obj);
    },
    next() {
      const first = this.gallery.shift();
      this.gallery = this.gallery.concat(first);
    },
    previous() {
      const last = this.gallery.pop();
      this.gallery = [last].concat(this.gallery);
    }
    // showImage(id, url, description) {
    //   var obj = {
    //     id: id,
    //     url: url,
    //     description: description
    //   };
    //   this.temp.push(obj);
    //   this.show = true;
    // }
  }
};
</script>

<style>
.carousel-view {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;

  width: 1280px;
  min-height: 720px;
}
.gallery {
  /* flex: 0 0 20em; */
  width: 1280px;
  height: 720px;
  margin: 1em;
  display: flex;
  justify-content: center;
  align-items: center;
  /* border: 0.1em dashed #000;
  border-radius: 50%; */
  transition: transform 0.3s ease-in-out;
}
.gallery:first-of-type {
  opacity: 0;
}
.gallery:last-of-type {
  opacity: 0;
}

.image {
  float: left;
  text-align: center;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
  border: 1px solid #ebebeb;
  margin: 5px;
}
</style>