<template>
  <div>
    <Header/>
    <div class="page">
      <div class="container">
        <nuxt/>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/header";
import "@/assets/base.css";
import "@/assets/global.css";

export default {

  components: {
    Header
  }
}

</script>

<style>

.page {
  padding: 2rem 0 5rem;
}

</style>
