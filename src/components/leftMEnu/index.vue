<template>
  <div class="leftMenu">
    <i-icon @click="showLeft = true" type="createtask_fill" size="28" color="#80848f" />
    <i-drawer mode="left" :visible="showLeft" @close="closeLeft">
      <div class="left-menu">
        <div class="menu-top">
          <img class="logo" src="" alt="">
          <span>记工时</span>
        </div>
        <ul class="menu-bottom">
          <li @click="toPage('index')">
            <i-icon type="activity_fill" size="28" color="#fff"></i-icon>
            <span>日历</span>
          </li>
          <li @click="toPage('place')">
            <i-icon type="activity_fill" size="28" color="#fff"></i-icon>
            <span>工地</span>
          </li>
          <li @click="toPage('receive')">
            <i-icon type="activity_fill" size="28" color="#fff"></i-icon>
            <span>应收</span>
          </li>
          <li @click="toPage('setting')">
            <i-icon type="activity_fill" size="28" color="#fff"></i-icon>
            <span>设置</span>
          </li>
        </ul>
      </div>
    </i-drawer>
  </div>
</template>


<script>
  import Calendar from 'mpvue-calendar'


  export default {
    data() {
      return {
        showLeft: false,
      }
    },
    components: {
      Calendar
    },
    methods: {
      toPage(to) {
        this.showLeft = false
        wx.navigateTo({
          url: `/pages/${to}/main`,
          success: function (res) {
            console.log("success")
          },
        })
      },
      closeLeft() {
        this.showLeft = false
      },

    }
  }
</script>

<style lang="stylus" scoped>
  .leftMenu {
    .left-menu {
      background: black;
      width: 65vw;
      height: 100vh;

      .menu-top {
        height: 200px;
        padding: 20px 0;
        text-align: center;
        color: #fff;

        .logo {
          background: red;
          width: 100px;
          height: 100px;
          display: block;
          margin: 0px auto;
          margin-bottom: 5px;

        }
      }

      .menu-bottom {
        color: #fff;
        display: flex;
        flex-direction: column;
        height: 200px;
        justify-content: space-between;
        align-items: center;

      }


    }
  }
</style>