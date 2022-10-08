<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :msg="finallyString" @ok="getChildInfo" />
  </div>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue, Watch } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';

@Component({
  name: 'App',
  components: {
    HelloWorld,
  },
})
export default class App extends Vue {
  // data
  public msg = '123456';

  // 声明组件参数的接口
  @Prop({ default: 1 }) test!: number;

  @Watch('msg', { deep: true })
  onChildChanged(val: string, oldVal: string) {
    console.log(val, oldVal)
  }

  public getChildInfo(event: any) {
    console.log(event.name)
  }

  mounted() {
    setTimeout(() => {
      this.finallyString = '哈哈哈哈'
    }, 3000)
  }

  // computed属性
  get finallyString() {
    return this.msg + 'finallyString computed' // 从哪获取
  }

  set finallyString(value) {
    console.log(value) // 怎么处理
  }

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
