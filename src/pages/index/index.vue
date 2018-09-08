<template>
  <div class="home">
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
    <Calendar :value="value" @next="next" @prev="prev" :events="events" @select="select" ref="calendar" @selectMonth="selectMonth"
      @selectYear="selectYear" />
    <div @click="toPage('addPlace')" class="addPlace">
      <i-icon type="add" size="68" color="#fff" />
    </div>
    <p style="text-align:center;">创建工地</p>

    <!-- <i-button>默认按钮</i-button>
    <button @click="setToday">返回今日</button>
    <button @click="dateInfo">日期信息</button> -->
  </div>
</template>


<script>
  import Calendar from 'mpvue-calendar'


  export default {
    data() {
      return {
        showLeft: false,
        // months: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
        disabledarr: ['2018-6-27', '2018-6-25'],
        value: [2018, 6, 7],
        begin: [2016, 1, 1],
        end: [2020, 1, 1],
        events: {
          '2018-6-7': '今日备注',
          '2018-6-8': '一条很长的明日备注'
        },
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
      selectMonth(month, year) {
        console.log(year, month)
      },
      prev(month) {
        console.log(month)
      },
      next(month) {
        console.log(month)
      },
      selectYear(year) {
        console.log(year)
      },
      setToday(val, val1, val2) {
        this.$refs.calendar.setToday();
      },
      select(val, val2) {
        console.log(val)
        console.log(val2)
      },
      dateInfo() {
        const info = this.$refs.calendar.dateInfo(2018, 8, 23);
        console.log(info);
      },
    }
  }
</script>

<style lang="stylus" scoped>
  .home {
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

    .addPlace {
      background: blue;
      width: 80px;
      height: 80px;
      margin: 0 auto;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 50%;

    }
  }
</style>