<template>
  <div id="index">
    <h1>Mini Gallery Kompas</h1>
    <div>
      <input type="text" v-model="title" style="margin-bottom:5px" />
    </div>
    <div>
      <input type="text" v-model="description" style="margin-bottom:5px" />
    </div>
    <div>
      <input type="text" v-model="url" style="margin-bottom:5px" />
    </div>

    <button @click="insertData()">Insert</button>
  </div>
</template>

<script>
export default {
  name: "Index",
  data: function() {
    return {
      message: "Some Message"
    };
  },
  methods: {}
};
</script>