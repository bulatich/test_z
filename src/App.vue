<template>
  <v-app>
    <test-app />
  </v-app>
</template>

<script>
import TestApp from "./components/TestApp";

export default {
  name: "App",
  components: {
    TestApp
  },
  data: () => ({})
};
</script>

