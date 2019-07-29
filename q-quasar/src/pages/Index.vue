<template>
  <q-page class="flex flex-center">
    <img alt="Quasar logo" src="~assets/quasar-logo-full.svg" />
  </q-page>
</template>

<style>
</style>

<script>
import axios from "axios";
axios.defaults.baseURL = "http://localhost:8000/api";
export default {
  name: "PageIndex",
  data: () => ({
    token: "5VpoMu5pzFi3x39fZ4UElIjNaB5Ce7COAHnoTDDyEepypY0omo8LUDF6Gtgp"
  }),
  methods: {
    testApi(method) {
      axios({
        method: method,
        url: "/test"
      }).then(response => {
        console.log(response);
      });
    },
    getUser() {
      axios({
        method: "get",
        url: "/user",
        headers: {
          Authorization: "Bearer " + this.token
        }
        // params: {
        //   api_token: this.token
        // }
      }).then(response => {
        console.log(response);
      });
    }
  },
  created() {
    this.getUser();
  }
};
</script>
