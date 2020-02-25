<template>
  <div id="index">
    <h1>Mini Gallery Kompas</h1>
    <div>
      <input type="text" v-model="title" style="margin-bottom:5px" placeholder="Title" />
    </div>
    <div>
      <input type="text" v-model="description" style="margin-bottom:5px" placeholder="Description" />
    </div>
    <div>
      <input type="text" v-model="url" style="margin-bottom:5px" placeholder="Url" />
    </div>

    <button @click="add()">Insert</button>
    <div class="carousel-view">
      <transition-group class="carousel" tag="div">
        <div v-for="g in gallery" class="gallery" :key="g.id">
          <div>
            <img v-bind:src="g.url" alt width="200" height="200" />
          </div>
        </div>
      </transition-group>
      <div class="carousel-controls">
        <button class="carousel-controls__button" @click="previous">prev</button>
        <button class="carousel-controls__button" @click="next">next</button>
      </div>
    </div>
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
      gallery: []
    };
  },
  methods: {
    add: function() {
      var obj = {
        id: this.id++,
        title: this.title,
        deskripsi: this.deskripsi,
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

  width: 24em;
  min-height: 25em;
}
.gallery {
  flex: 0 0 20em;
  height: 20em;
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
</style>