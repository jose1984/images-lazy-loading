<template>
  <img class="lazy-load-image" :src="img" alt>
</template>
<script>
export default {
  name: 'ImageLazyLoading',
  data() {
    return {
      img: ''
    }
  },
  mounted() {
    this.observer = new IntersectionObserver(async ([entry]) => {
      if (entry.isIntersecting) {
        this.observer.unobserve(entry.target)
        this.img = Math.round(Math.random()) ? await this.fetchDogImage() : await this.fetchCatImage()
      }
    })
    this.observer.observe(this.$el)
  },
  methods: {
    async fetchDogImage() {
      const res = await fetch('https://dog.ceo/api/breeds/image/random')
      const { message } = await res.json()
      return message
    },
    async fetchCatImage() {
      const res = await fetch('https://api.thecatapi.com/v1/images/search')
      const [ cat ] = await res.json()
      return cat.url
    }
  },
  destroyed() {
    this.observer.disconnect()
  }
};
</script>
