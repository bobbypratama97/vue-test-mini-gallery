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

    <div>
      <ul>
        <li v-for="g in gallery" v-bind:key="g.id">{{g.url}}</li>
      </ul>
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
    }
  }
};
</script>