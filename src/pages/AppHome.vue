<script>
import axios from "axios";
import { store } from "../store";

export default {
  data() {
    return {
      store,
      arrProjects: [],
    };
  },
  created() {
    axios.get(this.store.baseUrl + "api/projects/random").then((response) => {
      this.arrProjects = response.data.results;
    });
  },
};
</script>

<template>
  <div class="row row-cols-3 g-0">
    <div class="col" v-for="project in arrProjects" :key="project.id">
      <router-link
        class="d-block w-100 h-100"
        :to="{ name: 'projects.show', params: { slug: project.slug } }"
      >
        <img
          class="w-100 h-100"
          :src="store.getImageUrl(project.image)"
          :alt="project.title"
        />
      </router-link>
    </div>
  </div>
</template>

<style scoped>
/* TODO: fix style of grid (center and fill the screen with 100vh) */

.row {
  height: 70vh;
}

.col {
  height: calc(100% / 3);
}

img {
  object-fit: cover;
}
</style>
