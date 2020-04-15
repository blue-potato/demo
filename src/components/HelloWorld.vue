<template>
  <div class="bg">
    <div class="box" v-show="flag">
      <div class="title">
        <div class="title_item"
        v-for="(item, index) in bang" :key="index"
        :class="selindex == index ? 'active' : ''" 
        @click="select(index)">
        {{item.title}}</div>
      </div>
      <div class="scroll">
        <div class="scroll-item" v-for="item in 30" :key="item">内容{{selindex}}</div>
      </div>
      <div class="box-close" @click="flag = false">关闭</div>
    </div>
    <div class="tabBar">
      <div class="tab_btn" @click="flag = true">点击弹出</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selindex: 0,
      bang: [
        { title: '排行榜0' },
        { title: '排行榜1' },
        { title: '排行榜2' }
      ],
      flag: true
    }
  },
  methods: {
    select(index) {
      this.selindex = index
    }
  },
}
</script>
<style scoped>
.bg {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  background-color: rosybrown;
}
.title {
  display: flex;
  text-align: center;
}
.active{
  background-color: seagreen;
  color: #ffffff;
}
.title_item {
  flex: 1;
  margin: 10px 10px;
  border-radius: 6px;
  line-height: 30px;
}
.box {
  width: 80%;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
}
.scroll{
  height: 320px;
  overflow-y: auto;
}
.box-close {
  position: absolute;
  width: 50px;
  height: 50px;
  line-height: 50px;
  text-align: center;
  border-radius: 50%;
  left: 50%;
  transform: translate(-50%);
  bottom: -50px;
}
.tabBar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 38px;
  background-color: green;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding: 0 20px;
}
.tab_btn {
  color: red;
}
</style>