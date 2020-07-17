<template>
  <div>
    <p @click="emitTodo">我是子组件哦</p>
    <p>这是父组件给我的东西 {{email}}</p>
    <input type="checkbox" v-model="foo" value="some value" />
  </div>
</template>

<script lang="ts">
import {
  Component,
  Vue,
  Emit,
  Prop,
  Model,
  Watch
} from "vue-property-decorator";
@Component
export default class comp extends Vue {
  private foo: boolean = false;
  mounted() {
    this.$on("emit-todo", function(n) {
      console.log(n);
    });
    this.emitTodo("world");
  }
  @Watch("foo")
  private fooWatch(newval: string, old: string) {
    console.log(newval);
  }
  @Emit()
  emitTodo(n: string) {
    console.log(n,"hello");
  }
  @Prop({
    type: String,
    required: false,
    default: ""
  })
  email!: string;
  @Model("change", { type: Boolean }) checked!: boolean;
}
</script>

<style>
</style>