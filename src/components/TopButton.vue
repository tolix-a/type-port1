<template>
  <button class="top" @click="toTop" v-if="showTop">
    <img class="light-image" src='../../public/up_black.svg'/>
    <img class="dark-image" src="../../public/up.svg"/>
  </button>
</template>
<script>
export default {
  data() {
    return {
      showTop: false
    }
  },
  methods: {
    toTop(){
      window.scrollTo({ top: 0, behavior:'smooth' })
    },
    
    handleScroll() {
      const scrollTop = window.scrollY;
      this.showTop = scrollTop > 100;
    }
  },
  mounted(){
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>
<style lang="scss">
  .top{
    position: fixed;
    bottom: 8%;
    right: 5%;
    background: transparent;
    border: none;
    cursor: pointer;
    z-index: 10;
    transition: opacity 0.3s ease-in-out;

    .light-image{
      display: block;
    }
    .dark-image{
      display: none;
    }
  }
</style>