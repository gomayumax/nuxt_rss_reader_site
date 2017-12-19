<template>
  <div class="block">
    <h4>category</h4>
    <el-rate v-model="value" :colors="['#2F3D4D', '#64B486', '#4B7C6E']"></el-rate>
    <p>{{data.root}}</p>
  </div>
</template>

<script>
  export default {
    asyncData ({params}, callback) {
      var parseString = require('xml2js').parseString
      var xml = '<root>Hello xml2js!</root>'
      parseString(xml, (message, res) => {
        callback(null, {data: res})
      })
    },
    data () {
      return {
        value: null
      }
    }
  }
</script>

<style scoped>
  .block {
    padding: 0 20px;
  }
</style>
