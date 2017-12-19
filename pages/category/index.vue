<template>
  <div class="block">
    <h4>category</h4>
    <el-rate v-model="value" :colors="['#2F3D4D', '#64B486', '#4B7C6E']"></el-rate>
    <p>{{data.root}}</p>
    <ul>
      <li v-for="item in data">
        <a v-bind:href="item.link[0]">
          {{item.title[0]}}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    asyncData ({params}, callback) {
      axios.get(`https://rss.allabout.co.jp/aa/latest/ch/health/`)
        .then((res) => {
          var parseString = require('xml2js').parseString
          var xml = res.data
          parseString(xml, (message, xmlres) => {
            callback(null, {data: xmlres.rss.channel[0].item})
          })
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
