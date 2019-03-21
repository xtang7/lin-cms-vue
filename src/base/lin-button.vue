<template>
  <button class="l-button circle" :class="{[`icon-${iconPosition}`]: true, [`l-button--${type}`]: true, plain: plain}"
    @click="$emit('click')">
    <l-icon class="icon" v-if="icon && !loading" :name="icon"/>
    <l-icon class="loading icon" v-if="loading" name="loading"/>
    <div class="l-button-content">
      <slot/>
    </div>
  </button>
</template>
<script>
  import Icon from './icon'
  export default {
    name: 'LinButton',
    components: {
      'l-icon': Icon
    },
    props: {
      type: {
        type: String,
        default: 'default'
      },
      plain: {
        type: Boolean,
        default: false
      },
      icon: {},
      loading: {
        type: Boolean,
        default: false
      },
      iconPosition: {
        type: String,
        default: 'left',
        validator (value) {
          return value === 'left' || value === 'right'
        }
      }
    },
  }
</script>
<style lang="scss" scoped>
  @import './button.scss';
  .l-button { font-size: $font-size; height: $button-height; padding: 0 1em;
    border-radius: $border-radius;
    border: 1px solid $border-color;
    background: $button-bg;
    color: $button-color;
    display: inline-flex; justify-content: center; align-items: center;
    vertical-align: middle;
    &:hover { border-color: $border-color-hover; }
    &:active { background-color: $button-active-bg; }
    &:focus { outline: none; }
    > .l-button-content { order: 2; }
    > .icon { order: 1; margin-right: .1em; }

    &.icon-right {
      > .l-button-content { order: 1; }
      > .icon { order: 2; margin-right: 0; margin-left: .1em;}
    }
    .loading {
      @include spin;
    }
  }
  .l-button + .l-button {
    margin-left:10px;
  }
  .circle {
    border-radius: 50%;
    min-width:$button-height;
    padding: 0px;
  }
  .l-button--primary {
    background: $button-primary-bg;
    color: #fff;
    border: none;
    &.plain {
      color: $button-primary-plain-color;
      background: #fff;
      border: 1px solid $button-primary-plain-color;
    }
  }
  .l-button--success {
    background: $button-success-bg;
    color: #fff;
    border: none;
    &.plain {
      color: $button-success-plain-color;
      background: #fff;
      border: 1px solid $button-success-plain-color;
    }
  }
   .l-button--danger {
    background: $button-danger-bg;
    color: #fff;
    border: none;
    &.plain {
      color: $button-danger-plain-color;
      background: #fff;
      border: 1px solid $button-danger-plain-color;
    }
  }
   .l-button--info {
    background: $button-info-bg;
    color: #fff;
    border: none;
    &.plain {
      color: $button-info-plain-color;
      background: #fff;
      border: 1px solid $button-info-plain-color;
    }
  }
</style>