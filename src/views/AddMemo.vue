<template>
  <div>
    <input type="text" v-model="title" /><br />
    <input type="text" v-model="content" /><br />
    <input type="file" @change="selectFile" />
    <button @click="addMemo">Save</button>
  </div>
</template>

<script>
import memoApi from "../apis/memos";

export default {
  data() {
    return {
      title: "",
      content: "",
      file: "",
    };
  },
  methods: {
    selectFile() {
      this.file = this.$refs.file.files[0];
    },
    addMemo() {
      const data = new FormData();
      data.append("title", this.title);
      data.append("content", this.content);
      data.append("file", this.file);

      memoApi.addMemo(data).then((response) => {
        console.log(response.status);
        this.$router.push("/");
      });
    },
  },
};
</script>