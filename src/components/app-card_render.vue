<template>
  <div class="container-fluid">
    <div class="row justify-content-center">
      <div class="col-12 bg-light">
        <div class="row justify-content-center p-0 bg-dark">
          <div class="col-4 col-lg-3 p-3" v-for="(card, i) in cardList">
            <div class="card">
              <div class="container p-0">
                <img
                  :src="cardList[i].card_images[0].image_url"
                  class="img-fluid"
                />
              </div>
            </div>
            <div class="card-footer py-2">
              <div class="container text-center">
                <h5>
                  {{ cardList[i].name }}
                </h5>
              </div>
              <div class="container p-2 text-center">
                <span>
                  {{ cardList[i].archetype }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "card_render",
  props: ["cardList"],
  data() {
    return {
      lista: [1, 2, 3],
    };
  },
};
</script>
<style></style>
