<template>
  <div class="">
    <h2>這裡是後台管理頁面</h2>
    <div id="nav">
      <router-link to="/admin/products">後台產品列表</router-link> |
      <router-link to="/admin/coupons">後台酷碰劵列表</router-link> |
      <router-link to="/admin/order">訂單列表</router-link> |
      <router-link to="/">回前台</router-link> |
      <button class="btn" type="button" @click="signout">
        登出
      </button>
    </div>
    <router-view :token="token" v-if="checkSuccess"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      token: '',
      checkSuccess: false,
    };
  },
  created() {
    this.checkLogin();
  },
  methods: {
    checkLogin() {
      this.token = document.cookie.replace(/(?:(?:^|.*;\s*)token\s*=\s*([^;]*).*$)|^.*$/, '$1');
      // 將 Token 加入到 Headers 內
      this.axios.defaults.headers.common.Authorization = `Bearer ${this.token}`;

      const api = `${process.env.VUE_APP_APIPATH}/auth/check`;
      this.axios.post(api, {
        api_token: this.token,
      })
        .then((res) => {
          console.log(res);
          this.checkSuccess = true;
        }).catch((error) => {
          console.log(error.response);
          this.$router.push('/login');
        });
    },
    signout() {
      document.cookie = 'token=; expires=; path=/';
      this.$router.push('/');
    },
  },
};
</script>
