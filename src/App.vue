<template>
  <div class="container-fluid">
    <p>{{ archetypeSelected }}</p>
    <div class="container">
      <div class="row">
        <div class="col-3" v-for="card in cards">
          <div class="container">
            <img :src="card.card_images[0].image_url" class="w-100" />
          </div>
          <div class="container">
            <h3>
              {{ card.name }}
            </h3>
          </div>
          <div class="container">
            <h2>
              {{ card.archetype }}
            </h2>
          </div>
        </div>
      </div>
    </div>
  </div>
  <select v-model="archetypeSelected" @change="getSeletedArchetype">
    <option v-for="archetype in archetypes">
      <span>
        {{ archetype.archetype_name }}
      </span>
    </option>
  </select>
  <button @click="getCardsDataFromApi">click</button>
</template>
<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      apiURL: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
      apiArchetypesURL: "https://db.ygoprodeck.com/api/v7/archetypes.php",

      archetypeSelected: "",
      cards: [],
      archetypes: [],
      prova: "",
    };
  },
  // API URL

  methods: {
    getSeletedArchetype() {
      console.log(this.archetypeSelected);
    },
    getCardsDataFromApi() {
      axios
        .get(this.apiURL, {
          params: { archetype: this.archetypeSelected },
        })
        .then((response) => {
          this.cards = response.data.data;
          console.log(this.cards);
          console.log(this.prova);
          console.log(this.archetypeSelected);
        });
    },
  },
  mounted() {
    axios.get(this.apiArchetypesURL).then((response) => {
      this.archetypes = response.data;
      console.log(this.archetypes);
    });
  },
};
</script>

<style>
* {
  border: 1px solid black;
}
</style>
