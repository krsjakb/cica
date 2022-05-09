<template>
  <div>
    <b-container>
      <b-button variant="warning" @click="backButtonClicked">Vissza</b-button>
      <b-form @submit="onSubmit" @reset="onReset">
        <b-row>
          <b-form-group
            id="input-group-1"
            label="Név:"
            label-for="input-1"
            class="col-md-6 col-sm-12"
          >
            <b-form-input
              id="input-1"
              v-model="animal.name"
              type="text"
              placeholder="Név"
              required
            ></b-form-input>
          </b-form-group>
          <b-form-group
            id="input-group-2"
            label="Kép url:"
            label-for="input-2"
            class="col-md-6 col-sm-12"
          >
            <b-form-input
              id="input-2"
              v-model="animal.picture"
              type="text"
              placeholder="Kép url"
              required
            ></b-form-input>
          </b-form-group>
          <b-form-group
            id="input-group-3"
            label="Kor:"
            label-for="input-3"
            class="col-md-6 col-sm-12"
          >
            <b-form-input
              id="input-3"
              v-model="animal.age"
              type="number"
              placeholder="Kor"
              required
            ></b-form-input>
          </b-form-group>
          <b-form-group
            id="input-group-4"
            label="Szemszín:"
            label-for="input-4"
            class="col-md-6 col-sm-12"
          >
            <b-form-input
              id="input-4"
              v-model="animal.eyeColor"
              type="text"
              placeholder="Szemszín"
              required
            ></b-form-input>
          </b-form-group>
          <b-form-group
            id="input-group-5"
            label="Nem:"
            label-for="input-5"
            class="col-md-6 col-sm-12"
          >
            <b-form-select
              id="input-5"
              v-model="animal.gender"
              :options="genderOptions"
            ></b-form-select>
          </b-form-group>
          <b-form-group
            id="input-group-6"
            label="Faj:"
            label-for="input-6"
            class="col-md-6 col-sm-12"
          >
            <b-form-input
              id="input-6"
              v-model="animal.species"
              type="text"
              placeholder="Faj"
              required
            ></b-form-input>
          </b-form-group>
          <b-form-group
            id="input-group-7"
            label="Alfaj:"
            label-for="input-7"
            class="col-md-6 col-sm-12"
          >
            <b-form-input
              id="input-7"
              v-model="animal.breed"
              type="text"
              placeholder="Alfaj"
              required
            ></b-form-input>
          </b-form-group>
          <b-form-group
            id="input-group-8"
            label="Leírás:"
            label-for="input-8"
            class="col-md-6 col-sm-12"
          >
            <b-form-input
              id="input-8"
              v-model="animal.about"
              type="text"
              placeholder="Leírás"
              required
            ></b-form-input>
          </b-form-group>
        </b-row>
        <div class="float-right">
          <b-button type="submit" variant="success" class="mr-2"
            >Mentés</b-button
          >
          <b-button type="reset" variant="danger">Reset</b-button>
        </div>
      </b-form>
    </b-container>
  </div>
</template>

<script>
export default {
  name: "AddAnimal",
  props: {
    animalProp: {
      type: Object,
      required: false,
    },
  },
  data() {
    return {
      show: true,
      animal: {
        id: "",
        picture: "",
        age: null,
        eyeColor: "",
        name: "",
        gender: "",
        species: "",
        breed: "",
        about: "",
        favoriteFruit: "",
      },
      genderOptions: [
        {
          value: "",
          text: "Válassz egy opciót",
        },
        {
          value: "male",
          text: "Hím",
        },
        {
          value: "female",
          text: "Nőstény",
        },
      ],
    };
  },
  methods: {
    onSubmit() {
      if (this.animal.id === "") {
        this.animal.id = this.uuidv4();
      }
      this.$emit("animalAdded", this.animal);
    },

    uuidv4() {
      return ([1e7] + -1e3 + -4e3 + -8e3 + -1e11).replace(/[018]/g, (c) =>
        (
          c ^
          (crypto.getRandomValues(new Uint8Array(1))[0] & (15 >> (c / 4)))
        ).toString(16)
      );
    },

    onReset() {
      this.animal = {
        id: "",
        picture: "",
        age: null,
        eyeColor: "",
        name: "",
        gender: "",
        species: "",
        breed: "",
        about: "",
        favoriteFruit: "",
      };
    },
    backButtonClicked() {
      this.$emit("backButtonClicked");
    },
  },
  created() {
    if (this.animalProp) {
      this.animal = this.animalProp;
    }
  },
};
</script>

<style scoped></style>
