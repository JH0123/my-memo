<template>
  <div>
    <h1>Signin</h1>
    <from @submit.prevent="onSubmit(userid, password)">
      <input type="text" v-model="userid" placeholder="User Id" />
      <input type="password" v-model="password" placeholder="Password" />
      <input type="submit" value="Signin" />
    </from>
    <p>
      <i>{{ message }}</i>
    </p>
  </div>
</template>

<script>
export default {
  name: "Signin",
  data() {
    return {
      userid: "",
      password: "",
      message: "",
    };
  },
  methods: {
    onsubmit(userid, password) {
      this.$store
        .dispatch("signin", { userid, password })
        .then(() => {
          this.$router.push("/");
        })
        .catch(() => {
          this.message = "Signin Failed.";
        });
    },
  },
};
</script>