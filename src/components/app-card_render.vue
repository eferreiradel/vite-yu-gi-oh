<template>
  <div class="container-fluid">
    <div class="row p-0">
      <div class="col-12 col-lg-6 p-0">
        <div class="col-4 col-lg-5 p-3">
          <div class="card"></div>
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
    return {};
  },
  mounted() {
    console.log(cardLIst);
  },
};
</script>
<style></style>
