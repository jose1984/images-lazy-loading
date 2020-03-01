<template>
  <div class="intersection">Intersecting...</div>
</template>
<script>
export default {
  mounted() {
    this.observer = new IntersectionObserver(() =>
      this.$emit('onIntersecting')
    );
    this.observer.observe(this.$el);
  },
  destroyed() {
    this.observer.disconnect();
  }
};
</script>