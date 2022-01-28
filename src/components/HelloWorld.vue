<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>user id</h2>
    <div>{{ userId }}</div>
    <hr />
    <h2>URL----</h2>
    <div>{{ msg }}</div>
  </div>
</template>

<script>
// @ is an alias to /src
import liff from "@line/liff";

export default {
  name: "About",
  data() {
    return {
      msg: "",
      userId: "",
    };
  },
  mounted() {
    liff
      .init({
        liffId: "1656824759-Wq3mAOG4",
      })
      .then((res) => {
        console.log("res--> "+res);
        if (!liff.isLoggedIn()) liff.login();

        liff.getProfile().then((profile) => {
          const userId = profile.userId;
          this.userId = userId;
          this.msg = window.location.href;
        });
      })
      .catch((err) => {
        alert(err.code, err.message);
        alert("綁定異常，請聯絡作者");
      });
  },
  methods: {},
};

// url = https://vue-project-sample.herokuapp.com/
</script>
