<template>
  <div class="block">
    <h4>category select</h4>
    <ul>
      <li v-for="category in categories"><a v-bind:href="category.href">{{category.name}}</a></li>
    </ul>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        value: null,
        categories: [
          {name: '健康', href: '/category/health/'},
          {name: '一戸建て', href: '/category/house/'},
          {name: '国内旅行', href: '/category/domestic/'},
          {name: 'ダイエット', href: '/category/beautydiet/'},
          {name: 'ペット', href: '/category/pet/'},
          {name: 'ファッション', href: '/category/fashion/'}
        ]
      }
    }
  }
</script>

<style scoped>
  .block {
    padding: 0 20px;
  }
</style>
