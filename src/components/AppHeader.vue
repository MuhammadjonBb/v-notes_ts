<template lang="pug">
header.navbar
  .container
    .navbar-content
      router-link.navbar-logo(to="/") <span class="logo-item">V</span>-{{title}}
      ul.navbar-list
        li.navbar-item(v-for="link in links" :key="link.alias")
          router-link.navbar-link(:to="link.url") {{ link.title }}
</template>

<script lang="ts">
/* eslint-disable quotes */
import { links, app } from "@/_config";

export default {
  data() {
    return {
      links,
      title: app.title,
    };
  },
};
</script>

<style lang="scss" scoped>
.logo-item {
  color: #42b883;
}
</style>
