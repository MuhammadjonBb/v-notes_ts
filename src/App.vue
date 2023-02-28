<template lang="pug">
AppHeader
.wrapper-content
  .container
    router-view
AppFooter
</template>

<script lang="ts">
import AppHeader from "@/components/AppHeader.vue";
import AppFooter from "@/components/AppFooter.vue";

export default {
  components: { AppHeader, AppFooter },
};
</script>

<style></style>
