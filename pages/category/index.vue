<template>
  <div>
    <h4>category select</h4>
      <el-col v-for="category in categories" :span="24" class="el-col">
        <a v-bind:href="category.href">
        <div class="grid-content bg-purple">
            {{category.name}}
        </div>
        </a>
      </el-col>
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

<style>
  a {
    text-decoration: none;
  }
  .el-row {
    margin-bottom: 20px;
  &:last-child {
     margin-bottom: 0;
   }
  }
  .el-col {
    border-radius: 4px;
    padding-bottom: 10px;
  }
  .bg-purple {
    background: #d3dce6;
  }

  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
</style>
