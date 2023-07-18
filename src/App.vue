<script>
import ProjectList from "./components/ProjectList.vue";

export default {
  components: {
    ProjectList,
  },
};
</script>

<template>
  <div class="container">
    <h1>Boolpress</h1>
    <ProjectList> </ProjectList>
  </div>
</template>

<style lang="scss">
@import "bootstrap/scss/bootstrap";
</style>
