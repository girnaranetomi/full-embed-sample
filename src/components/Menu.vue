<template>
  <div class="Menu" :class="{Menu_opened: opened}">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "Menu",

    props: {
      opened: Boolean,
      toggleButton: null
    },

    mounted() {
      document.addEventListener('click', this.handleDocumentClick, true);
      Workato.on('click', this.handleIFrameClick);
    },

    destroyed() {
      document.removeEventListener('click', this.handleDocumentClick, true);
      Workato.off('click', this.handleIFrameClick);
    },

    methods: {
      toggleOpened(flag = !this.opened) {
        this.$emit('update:opened', flag);
      },

      handleDocumentClick(event) {
        if (!this.opened) {
          return;
        }

        if (this.$el === event.target || this.$el.contains(event.target)) {
          return;
        }

        let toggleElem;

        if (this.toggleButton) {
          toggleElem = this.toggleButton.$el || this.toggleButton;
        }

        if (toggleElem && (toggleElem === event.target || toggleElem.contains(event.target))) {
          return;
        }

        this.toggleOpened(false);
      },

      handleIFrameClick() {
        this.toggleOpened(false);
      }
    }
  }
</script>

<style lang="scss">
  .Menu {
    position: absolute;
    visibility: hidden;
    transition: opacity .3s ease, visibility .3s ease;
    background: #fff;
    box-shadow: 0 3px 5px 0 rgba(0, 0, 0, 0.2);
    padding: 35px;
    opacity: 0;
    top: 50px;
    left: 5px;

    &_opened {
      visibility: visible;
      opacity: 1;
      z-index: 100;
    }
  }
</style>
