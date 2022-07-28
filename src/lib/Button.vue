<template>
  <button class="sky-button" :class="classes">
    <slot />
  </button>
</template>

<script lang="ts">
import { computed } from 'vue';
export default {
  props: {
    theme: {
      type: String,
      default: "button",
    },
    size:{
      type:String,
      default:"normal",
    },
    level:{
      type:String,
      default:"normal",
    },
  },
  setup(props){
    const {theme,size,level} = props;
    const classes = computed(()=>{
      return {
        [`theme-${theme}`]:theme,
        [`size-${size}`]:size,
        [`level-${level}`]:level,
      }
    })
    return{classes}
  }
  
};
</script>

<style lang="scss">
$h: 32px;
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$red:#f00;
$radius: 4px;
.sky-button {
  box-sizing: border-box;
  height: $h;
  padding: 0 12px;
  cursor: pointer;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  white-space: nowrap;
  background: white;
  color: $color;
  border: 1px solid $border-color;
  border-radius: $radius;
  box-shadow: 0 1px 0 fade-out(black, 0.95);
  transition: background 250ms;
  & + & {
    margin-left: 8px;
  }
  &:hover,
  &:focus {
    color: $blue;
    border-color: $blue;
  }
  &:focus {
    outline: none;
  }
  &::-moz-focus-inner {
    border: 0;
  }
  &.sky-theme-link{
    border-color: transparent;
    box-shadow: none;
    color: $blue;
    &:hover,&:focus{
      color: lighten($blue, 10%);
    }
  }
  &.sky-theme-text{
    border-color: transparent;
    box-shadow: none;
    color: inherit;
    &:hover,
    &:focus{
      background: darken(white, 5%);;
    }
  }
   &.sky-size-big {
    font-size: 24px;
    height: 48px;
    padding: 0 16px;
  }
  &.sky-size-small {
    font-size: 12px;
    height: 20px;
    padding: 0 4px;
  }
   &.sky-theme-button {
    &.sky-level-main {
      background: $blue;
      color: white;
      border-color: $blue;
      &:hover,
      &:focus {
        background: darken($blue, 10%);
        border-color: darken($blue, 10%);
      }
    }
    &.sky-level-danger {
      background: $red;
      border-color: $red;
      color: white;
      &:hover,
      &:focus {
        background: darken($red, 10%);
        border-color: darken($red, 10%);
      }
    }
  }
  &.sky-theme-link {
    &.sky-level-danger {
      color: $red;
      &:hover,
      &:focus {
        color: darken($red, 10%);
      }
    }
  }
  &.sky-theme-text {
    &.sky-level-main {
      color: $blue;
      &:hover,
      &:focus {
        color: darken($blue, 10%);
      }
    }
    &.sky-level-danger {
      color: $red;
      &:hover,
      &:focus {
        color: darken($red, 10%);
      }
    }
  }
}
</style>
