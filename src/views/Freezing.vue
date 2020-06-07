<template>
  <div class="home">
    <LeftSidebar></LeftSidebar>
    <img alt="Vue logo" src="../assets/logo.png" />
    <FreezingList msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import FreezingList from "@/components/FreezingList.vue";

export default {
  name: "Home",
  components: {
    FreezingList
  }
};
</script>
