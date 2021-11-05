<template>
  <v-card color="rgb(255, 255, 255, 0.2)" class="rounded-xl">
    <v-img :src="postData.imgUrl"> </v-img>
    <v-card-title>
      {{ postData.title }}
    </v-card-title>
    <v-card-text>
      {{ postData.text }}
    </v-card-text>
  </v-card>
</template>

<script lang="ts">
export default {
  props: ["postData"],
  data: () => ({
    //
  }),
};
</script>

<style scoped>
.v-card__text,
.v-card__title {
  word-break: normal; /* maybe !important  */
}
</style>
