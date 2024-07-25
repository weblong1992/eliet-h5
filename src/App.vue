<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
  name: "App",
  mounted() {
    window.addEventListener("beforeunload", this.fn);
  },
  methods: {
    fn() {
      //回到顶部
      window.scrollTo(0, 0);
    },
  },
};
</script>

<style lang="scss">
html,
body,
#app {
  // height: 100%;
  width: 100%;
}

* {
  padding: 0;
  margin: 0;
}
</style>
