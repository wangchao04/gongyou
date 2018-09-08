<template>
  <div class="addPlace">
    <div class="head">新建工地</div>
    <i-button @click="toHome">取消</i-button>
     <i-button @click="toHome">保存</i-button>
    <!-- <a href="/pages/index/main" class="home">去往首页</a> -->
  </div>
</template>

<script>
// Use Vuex
import store from './store'

export default {
  computed: {
    count () {
      return store.state.count
    }
  },
  methods: {
      toHome() {
               wx.navigateTo({
                    url: '/pages/index/main',
                    success: function(res){
                        console.log("success")
                    },
                })
          },
    increment () {
      store.commit('increment')
    },
    decrement () {
      store.commit('decrement')
    }
  }
}
</script>

<style>
.counter-warp {
  text-align: center;
  margin-top: 100px;
}
.home {
  display: inline-block;
  margin: 100px auto;
  padding: 5px 10px;
  color: blue;
  border: 1px solid blue;
}
</style>
