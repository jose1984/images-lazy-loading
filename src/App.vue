<template>
  <div id="app">
    <ImageLazyLoading v-for="index in items" :key="index" />
    <Intersection @onIntersecting="items = items + 10"/>
  </div>
</template>

<script>
import ImageLazyLoading from './components/ImageLazyLoading'
import Intersection from './components/Intersection'

export default {
  name: 'App',
  components: {
    ImageLazyLoading,
    Intersection
  },
  data() {
    return {
      items: 10
    }
  }
}
</script>
<style>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.lazy-load-image {
  margin: 1em;
  min-height: 250px;
  max-width: 100%;
  box-shadow: 0px 0px 13px 0px rgba(0, 0, 0, 0.48);
}
</style>
