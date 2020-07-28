<template>
  <div id="app">
    <loading :active.sync="isLoading"></loading>
    <!-- <div id="nav">
      <router-link to="/">前台</router-link> |
      <router-link to="/admin">後台</router-link> |
    </div> -->
    <router-view />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isLoading: false,
    };
  },
  mounted() {
    // this.isLoading = true;
    // eslint-disable-next-line max-len
    // this.axios.get(`${process.env.VUE_APP_APIPATH}/${process.env.VUE_APP_UUID}/ec/products`).then((res) => {
    //   console.log(res);
    //   this.isLoading = false;
    // });
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
