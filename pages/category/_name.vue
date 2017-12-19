<template>
  <div>
    <el-row>
      <el-col :span="8" v-for="item in data" :key="o" :offset="index > 0 ? 2 : 0">
        <el-card :body-style="{ padding: '0px' }">
          <div style="padding: 14px;">
            <span>{{item.title[0]}}</span>
            <div class="bottom clearfix">
              <time class="time">{{ item.pubDate[0] }}</time>
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