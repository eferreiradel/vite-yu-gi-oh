<template>
  <card_render :cardList="cardList"></card_render>
</template>

<script>
// axios
import axios from "axios";
// components
import card_render from "./components/app-card_render.vue";
export default {
  name: "App",
  data() {
    return {
      cardList: "",
    };
  },
  components: {
    card_render,
  },
  mounted() {
    axios
      .get("https://db.ygoprodeck.com/api/v7/cardinfo.php")
      .then((response) => {
        this.cardList = response.data.data;
        console.log(this.cardList[0].card_images[0].image_url);
      });
  },
};
</script>

<style scoped lang="scss"></style>
