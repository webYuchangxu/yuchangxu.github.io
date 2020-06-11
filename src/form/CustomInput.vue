<template>
  <div>
    <!-- 自定义组件要实现v-model,必须实现value,@input -->
    <!-- $attrs 内存储非v-model绑定的值  {type:'password'} -->
    <input v-bind="$attrs" :value='value' @input="onInput" />
  </div>
</template>

<script>
export default {
  inheritAttrs:false,
  props: {
    value: {
      type: String,
      default: ""
    }
  },
  methods: {
    onInput(e) {
      // 通知父组件数值变化
      this.$emit("input", e.target.value);

      // 通知FormItem校验
      this.$parent.$emit('validate')
    }
  }
};
</script>

<style>
</style>