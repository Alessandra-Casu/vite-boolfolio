<script>
import axios from "axios";

export default {
  data() {
    return {
      arrProjects: [],
      nPage: 1,
    };
  },
  created() {
    //richiesta dati al server
    axios
      .get("http://127.0.0.1:8000/api/projects", {
        params: {
          page: this.nPage,
        },
      })
      .then((response) => (this.arrProjects = response.data.data));
  },
};
//this.arrProjects = response.data.data
</script>

<template>
  <h2>questi sono i nostri progetti</h2>
  <ul>
    <li v-for="project in arrProjects" :key="project.id">
      {{ project.title }}
    </li>
  </ul>
</template>

<style></style>
