<template>
  <div>
    <el-col :span="8" v-for="item in data" :key="o" :offset="index > 0 ? 2 : 0">
      <el-card :body-style="{ padding: '0px' }">
        <div style="padding: 14px;">
          <span>{{item.title[0]}}</span>
          <div class="bottom clearfix">
            <time class="time">{{ item.pubDate[0] }}</time>
          </div>
        </div>
      </el-card>
    </el-col>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    asyncData ({params}, callback) {
      axios.get(`https://rss.allabout.co.jp/aa/latest/ch/${params.name}`)
        .then((res) => {
          var parseString = require('xml2js').parseString
          var xml = res.data
          parseString(xml, (message, xmlres) => {
            callback(null, {data: xmlres.rss.channel[0].item})
          })
        })
        .catch((e) => {
          var result = { statusCode: 404, message: 'ページが見つかりません' }
          callback(result)
        })
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

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }

  .clearfix:after {
    clear: both
  }
</style>