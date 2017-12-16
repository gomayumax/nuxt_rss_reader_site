<template>
  <div>
    <el-row>
      <el-col :span="8" v-for="file in data" :key="o" :offset="index > 0 ? 2 : 0">
        <el-card :body-style="{ padding: '0px' }">
          <img v-bind:src="'http://xn--3ur52o1bb7099d.xn--u9jb933vm9i.com/images/' + file.name + ''" class="image" />
          <div style="padding: 14px;">
            <span>Yummy hamburger</span>
            <div class="bottom clearfix">
              <time class="time">{{ currentDate }}</time>
              <el-button type="text" class="button">Operating button</el-button>
            </div>
          </div>
        </el-card>
      </el-col>
    </el-row>
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
    },
    data () {
      return {
        currentDate: new Date()
      }
    }
  }
</script>

<style>
  .time {
    font-size: 13px;
    color: #999;
  }

  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 100%;
    height: 120px;
    display: block;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }

  .clearfix:after {
    clear: both
  }
</style>