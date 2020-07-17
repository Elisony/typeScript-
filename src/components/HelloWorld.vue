<template>
  <div id="app">
    <p>我是父组件</p>
    <button @click="age">+</button>
    <p>{{value}}</p>
    <button @click="age">-</button>
    <compne :email="email" @emitTodo="add"></compne>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch, Emit } from "vue-property-decorator";
import compne from "../components/compne.vue";
@Component({
  components: {
    compne
  }
})
export default class App extends Vue {
  private value: number = 1;
  private email: string = "123456789@qq.com";
  private picker: any = "";
  age() {
    this.value++;
    console.log(this.picker);
  }
  add(value) {
    console.log(value);
  }
  @Watch("value")
  private valueWatch(newval: string, old: string) {
    console.log(newval, old);
  }
}
</script>