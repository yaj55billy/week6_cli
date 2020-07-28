<template>
  <div class="">
    <h2>這裡是後台產品頁面</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [],
    };
  },
  props: ['token'],
  created() {
    // this.token = document.cookie.replace(/(?:(?:^|.*;\s*)token\s*=\s*([^;]*).*$)|^.*$/, '$1');
    // // 將 Token 加入到 Headers 內
    // this.axios.defaults.headers.common.Authorization = `Bearer ${this.token}`;
    const api = `${process.env.VUE_APP_APIPATH}/${process.env.VUE_APP_UUID}/admin/ec/products`;
    this.axios.get(api).then((res) => {
      this.products = res.data.data;
    });
  },
};
</script>
