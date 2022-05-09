<template>
  <div class="h-100 pb-2">
    <b-card
      :title="animal.name"
      :img-src="animal.picture"
      :img-alt="animal.breed"
      img-top
      tag="article"
      class="mb-2 h-100"
    >
      <b-card-text class="margin-bottom-60">
        <p>Faj: {{ animal.species }}</p>
        <p>Alfaj: {{ animal.breed }}</p>
        <p>Nem: {{ animal.gender }}</p>
        <p>Szemszín: {{ animal.eyeColor }}</p>
        <p>Kor: {{ animal.age }}</p>
        <p>Kedvenc gyümölcs: {{ animal.favoriteFruit }}</p>
        <p>Leírás: {{ animal.about }}</p>
      </b-card-text>

      <b-col align-self="end" class="bottom-button-container">
        <b-button class="w-50" @click="editClicked" variant="primary"
          >Szerkesztés</b-button
        >
        <b-button class="w-50" @click="animalDeleteClicked" variant="danger"
          >Törlés</b-button
        >
      </b-col>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "AnimalItem",
  props: {
    animal: {
      type: Object,
      required: true,
    },
  },
  methods: {
    animalDeleteClicked() {
      this.$emit("deleteClicked", this.animal);
    },
    editClicked() {
      this.$emit("editClicked", this.animal);
    },
  },
};
</script>

<style scoped>
.card-img-top {
  width: 100%;
  height: 35vw;
  object-fit: cover;
}

.bottom-button-container {
  position: absolute;
  padding: 0;
  bottom: 0;
  left: 0;
  width: 100%;
}

.margin-bottom-60 {
  margin-bottom: 60px;
}
</style>
