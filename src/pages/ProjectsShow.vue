<script>
import axios from "axios";
import { store } from "../store";
import { DateTime } from "luxon";
import App404 from "./App404.vue";

export default {
  components: {
    App404,
  },
  data() {
    return {
      project: null,
      store,
      luxon: DateTime,
      is404: false,
    };
  },
  created() {
    // richiesta axios per i dati del post
    // esempio: http://localhost:8000/api/posts/iusto-hic-libero-culpa-sit-similique
    axios
      .get(this.store.baseUrl + "api/projects/" + this.$route.params.slug)
      .then((response) => {
        if (response.data.success) {
          this.project = response.data.results;
        } else {
          // this.$router.push({ name: 'page404' });
          this.is404 = true;
        }
      });
  },
};
</script>

<template>
  <App404 v-if="is404" />
  <template v-else-if="post">
    <h1>{{ project.title }}</h1>
    <h2>Last modified: {{ this.luxon.now().toFormat("dd/MM/yyyy") }}</h2>
    <img :src="this.store.getImageUrl(project.image)" :alt="project.title" />
    <p>{{ project.content }}</p>
  </template>
</template>

<style></style>
