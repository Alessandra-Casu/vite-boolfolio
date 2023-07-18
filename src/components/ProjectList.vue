<script>
import axios from "axios";
import PostCard from "./ProjectCard.vue";
import { store } from "../store";

export default {
  components: {
    ProjectCard,
  },
  data() {
    return {
      arrProjects: [],
      currentPage: 1,
      nPages: 0,
      store,
    };
  },
  methods: {
    toPrevPage() {
      this.currentPage != 1 ? this.currentPage-- : null;
    },
    toNextPage() {
      this.currentPage != this.nPages ? this.currentPage++ : null;
    },
    getProjects() {
      axios
        .get(this.store.baseUrl + "api/projects", {
          params: {
            page: this.currentPage,
          },
        })
        .then((response) => {
          this.arrProjects = response.data.results.data;
          this.nPages = response.data.results.last_page;
        });
    },
  },
  created() {
    // richiesta dati al server
    this.getProjects();
  },
  watch: {
    currentPage() {
      this.getProjects();
    },
  },
};
</script>

<template>
  <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-4 mb-5">
    <div class="col" v-for="project in arrProjects" :key="project.id">
      <PostCard :objProject="project" />
    </div>
  </div>

  <nav>
    <ul class="pagination">
      <li class="page-item" :class="{ disabled: currentPage == 1 }">
        <a class="page-link" @click="toPrevPage">Previous</a>
      </li>

      <li
        v-for="page in nPages"
        :key="page"
        class="page-item"
        :class="{ active: page == currentPage }"
      >
        <a class="page-link" href="#" @click="currentPage = page">
          {{ page }}
        </a>
      </li>

      <li class="page-item" :class="{ disabled: currentPage == nPages }">
        <a class="page-link" href="#" @click="toNextPage">Next</a>
      </li>
    </ul>
  </nav>
</template>

<style></style>
