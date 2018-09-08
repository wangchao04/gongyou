<template>
  <div class="place">
    <leftMenu></leftMenu>
    工地
    <ul>
      <li >
        <i-swipeout i-class="i-swipeout-demo-item" :actions="actions" @change="menuClick">
          <div @click="toPage('placeDetail')" slot="content">
            <p>真大路5203846383</p>
            <p>水电管|小时制</p>
            <p>2018.12.12 入场</p>
          </div>
        </i-swipeout>
      </li>

    </ul>

    <i-modal title="结账" :visible="visible" @ok.stop="handleClose1" @cancel.stop="handleClose1">
      应收
    </i-modal>

  </div>
</template>


<script>
  import leftMenu from '@/components/leftMenu/index'


  export default {
    data() {
      return {
        visible: false,
        actions: [{
            name: '结账',
            color: '#fff',
            fontsize: '20',
            width: 100,
            background: '#ed3f14'
          },
          {
            name: '记工',
            width: 100,
            color: '#80848f',
            fontsize: '20',
          },
          {
            name: '删除',
            width: 100,
            color: 'red',
            fontsize: '20',
          }
        ]

      }
    },
    components: {
      leftMenu
    },
    methods: {
      toPage(to) {
        wx.navigateTo({
          url: `/pages/${to}/main`,
          success: function (res) {
            console.log("success")
          },
        })
      },
      handleClose1() {
        this.visible = false
      },
      menuClick(val) {
        if (val.target.index == 0) {
          this.visible = true
        } else if (val.target.index == 1) {
          this.toPage('workTime')
        } else {

        }

      }
    }
  }
</script>

<style lang="stylus" scoped>

</style>