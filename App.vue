<template>
  <div class="app">
    <div class="container">
      <router-view></router-view>
    </div>
    <div class="footer">
      <cube-tab-bar
        v-model="selectedLabelDefault"
        :data="tabs"
        @click="clickHandler"
        @change="changeHandler">
      </cube-tab-bar>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      selectedLabelDefault: '/',
      tabs: [{
        label: 'Home',
        value: '/',
        icon: 'iconfont icon-15',
      }, {
        label: '我的课程',
        value: '/course',
        icon: 'iconfont icon-19',
      }, {
        label: '个人中心',
        value: '/profile',
        icon: 'cubeic-vip',
      }, {
        label: 'Me',
        icon: 'cubeic-person',
      }],
    };
  },
  watch: {
    $route: {
      handler(to, from) {
        console.info('要查看的to', from);
        this.selectedLabelDefault = to.path;
      },
      immediate: true,
    },
  },
  methods: {
    clickHandler(label) {
      // if you clicked home tab, then print 'Home'
      console.log(label);
    },
    changeHandler(label) {
      this.$router.push(label);
      // if you clicked different tab, this methods can be emitted
    },
  },
};
</script>
<style lang="stylus">
html, body, .app
  width 100%
  height 100%
.app
  display flex
  flex-direction column
  .container
    flex 1
    overflow scroll
</style>
