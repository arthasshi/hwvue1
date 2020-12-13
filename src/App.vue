<template>
  <div id="app">
    {{message.name}}
    <span v-bind:title="message.name">我是span标签</span>
    <div v-for="(item,index) in arr" :key="index">{{item}}</div>
    <div v-if="false">我是if指令</div>
    <div v-else-if="true">我是if指令 else if 分支</div>
    <div v-else>我是if指令的 else分支</div>
    <!-- <div v-bind:class="[index == 1?cls1:index==2?cls2:index==3?cls3:'',cls]" v-on:click="test">点我</div> -->
    <input type="text" v-model.number="val" />
    <select v-model="ope">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <input type="text" v-model.number="val1" />
    <!-- <div v-on:click="computeResult">计算</div> -->
    <div v-if="ope == '+'">我是运算结果：{{val+val1}}</div>
    <div v-if="ope == '-'">我是运算结果：{{val-val1}}</div>
    <div v-if="ope == '*'">我是运算结果：{{val*val1}}</div>
    <div v-if="ope == '/'">我是运算结果：{{val/val1}}</div>
    <!-- <div v-else>请选择运算符</div> -->
    <div class="item" v-for="item in news" :key="item.index">
      <div
        v-bind:class="[item.index==1?'cls1':item.index==2?'cls2':item.index==3?'cls3':'cls']"
      >{{item.index}}</div>
      <div>{{item.title}}</div>
      <div>{{item.count}}万</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      message: {
        name: "hello"
      },
      val: 0,
      val1: 0,
      sum: 0,
      ope: "+",
      isBtn: false,
      arr: [11, 22, 33, 44, 55],
      news: [
        {
          index: 1,
          title: "31省",
          count: 477
        },
        {
          index: 2,
          title: "嫦娥5号",
          count: 477
        },
        {
          index: 3,
          title: "黑龙江",
          count: 477
        },
        {
          index: 4,
          title: "夙愿案",
          count: 477
        }
      ]
    };
  },
  methods: {
    test() {
      console.log("点击了按钮");
    },
    computeResult() {
      switch (this.ope) {
        case "+":
          this.sum = this.val + this.val1;
          break;
        case "-":
          this.sum = this.val - this.val1;
          break;
        case "*":
          this.sum = this.val * this.val1;
          break;
        case "/":
          this.sum = this.val / this.val1;
          break;
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.btn {
  color: aqua;
  cursor: pointer;
}
.item {
  width: 400px;
  height: auto;
  background: #f5f5f5;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.cls {
  color: #2c3e50;
}
.cls1 {
  color: aquamarine;
}
.cls2 {
  color: blue;
}
.cls3 {
  color: bisque;
}
</style>
