<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <Post
        v-for="(postData, index) in posts"
        :key="index"
        :postData="postData"
        class="mx-4 my-6"
      >
      </Post>
    </v-col>
  </v-row>
</template>

<script>
import facts from "~/static/facts.js";

export default {
  mounted() {
    this.getRandomDogImage();
    this.getRandomCatImage();
    this.geAPOD();
    this.getRandomFact();
  },
  data: () => ({
    posts: [],
  }),
  methods: {
    async getRandomDogImage() {
      const imgData = await this.$axios.$get(
        "https://random.dog/woof.json?filter=mp4,webm"
      );
      console.log(imgData);
      this.posts.push({
        title: "Here's a random dog fact, happy scrolling! 🐶",
        text: facts.dogFacts[Math.floor(Math.random() * facts.dogFacts.length)],
        imgUrl: imgData.url,
      });
    },
    async getRandomCatImage() {
      const imgData = await this.$axios.$get(
        "https://aws.random.cat/meow?ref=apilist.fun"
      );
      console.log(imgData);
      this.posts.push({
        title: "Here's a random cat fact, happy scrolling! 🐱",
        text: facts.catFacts[Math.floor(Math.random() * facts.catFacts.length)],
        imgUrl: imgData.file,
      });
    },
    async geAPOD() {
      const imgData = await this.$axios.$get(
        "https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY"
      );
      console.log(imgData);
      this.posts.push({
        title: "Astronomy picture of the day from NASA! 🚀",
        imgUrl: imgData.url,
      });
    },
    async getRandomFact() {
      var options = {
        method: "GET",
        url: "https://facts-by-api-ninjas.p.rapidapi.com/v1/facts",
        headers: {
          "x-rapidapi-host": "facts-by-api-ninjas.p.rapidapi.com",
          "x-rapidapi-key":
            "9fc8b6a812mshb4391c1831ff2a1p128f0djsne2b9e5faba6b",
        },
      };

      const imgData = await this.$axios.request(options);
      console.log(imgData);
      this.posts.push({
        title: "Some random fact !",
        text: imgData.data[0].fact + ".",
      });
    },
  },
};
</script>
