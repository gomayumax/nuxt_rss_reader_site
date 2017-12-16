<template>
  <div>
    <ul>
      <li v-for="file in data">{{file.name}}</li>
    </ul>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    asyncData ({params}, callback) {
      axios.get(`http://xn--3ur52o1bb7099d.xn--u9jb933vm9i.com/images.json`)
        .then((res) => {
          callback(null, {data: res.data.general})
        })
    }
  }
</script>

<style>
</style>