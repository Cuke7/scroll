<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title>Scroll 📜</v-toolbar-title>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    //
  }),
};
</script>

<style>
.v-main {
  background-image: linear-gradient(
    to right,
    #0f7600,
    #00764e,
    #007280,
    #00699a,
    #0e5b97
  );
}

.v-main {
  background-image: url("/background.jpg");
  background-repeat: repeat;
}
</style>
