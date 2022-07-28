<template>
  <div :size="size">
    <button v-bind="reset" >
      <slot />
    </button>
  </div>
</template>

<script lang="ts">
export default{
  inheritAttrs:false,
  props:{},
  setup(props,context){
    const {size,...reset} = context.attrs;
    return {size,reset}
  }

}
</script>

<style lang="scss" scoped>
div{
  border: 1px solid;
}
</style>
