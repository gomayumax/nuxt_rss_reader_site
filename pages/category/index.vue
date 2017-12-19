<template>
  <div class="block">
    <h4>category</h4>
    <el-rate v-model="value" :colors="['#2F3D4D', '#64B486', '#4B7C6E']"></el-rate>
  </div>
</template>

<script>
  export default {

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
