<template>
  <div class="widget">
    <header @click.prevent="toggle">
      <span class="summary" v-if="!open"><slot name="summary"></slot></span>
      <slot name="header"></slot>
    </header>
    <section v-if="open">
      <slot name="body"></slot>
    </section>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        open: true,
      };
    },
    methods: {
      toggle() {
        this.open = !this.open;
      },
    },
  };
</script>

<style lang="scss">
  .widget {
    margin-bottom: 10px;
    font-family: $widget-font-family;
    color: $widget-color;
    transition: color 0.2s ease-in-out, opacity 0.5s ease-in-out;
    background: $widget-background;
    font-size: 9pt;
    > header {
      cursor: pointer;
      background: $widget-header-background;
      transition: background 0.2s ease-in-out, opacity 0.5s ease-in-out;
      padding: 5px 10px;
      font-weight: bold;
      .summary {
        float: right;
        font-weight: normal;
      }
    }
    > section {
      max-height: 250px;
      overflow: auto;
      padding: 10px 10px;
      ul {
        list-style-type: none;
        margin: 0;
        padding: 0;
      }
    }
    &:hover {
      color: $widget-hover-color;
      > header {
        background: $widget-header-hover-background;
      }
    }
  }
</style>
