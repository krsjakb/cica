<template>
  <div>
    <div v-show="!editOrAddAnimalVisible">
      <div>
        <b-button
          variant="success"
          @click="
            {
              editOrAddAnimalVisible = !editOrAddAnimalVisible;
              selectedAnimal = null;
            }
          "
          >Hozzáadás</b-button
        >
      </div>

      <div class="row m-2">
        <div
          v-for="animalItem in animals"
          :key="animalItem.id"
          class="col-lg-3 col-sm-12 col-md-6"
        >
          <div class="h-100">
            <animal-item
              :animal="animalItem"
              @deleteClicked="animalDeleteClicked"
              @editClicked="animalEditClicked"
            />
          </div>
        </div>
      </div>
    </div>
    <div v-if="editOrAddAnimalVisible">
      <edit-or-add-animal
        :animalProp="selectedAnimal"
        @backButtonClicked="editOrAddAnimalVisible = !editOrAddAnimalVisible"
        @animalAdded="animalAdded"
      ></edit-or-add-animal>
    </div>
  </div>
</template>

<script>
import AnimalItem from "../../components/AnimalItem.vue";
import EditOrAddAnimal from "./EditOrAddAnimal.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Animals",
  components: {
    AnimalItem,
    EditOrAddAnimal,
  },
  data() {
    return {
      animals: [
        {
          id: "6278f67cc35556a07cea92a4",
          picture:
            "https://www.thesprucepets.com/thmb/68QXL78FwHtbXzGVQ0F4NTanhS0=/2121x1193/smart/filters:no_upscale()/peterpancakeGettyImages-638917674-ee473ffc1c3d4b65a568f9b4c1a4506b.jpg",
          age: 12,
          eyeColor: "blue",
          name: "Norma Leonard",
          gender: "female",
          species: "cat",
          breed: "bambino",
          about:
            "Ea irure deserunt sit exercitation occaecat. Cupidatat ad laboris ipsum enim in sit nostrud ullamco in pariatur fugiat incididunt. Tempor sit velit fugiat proident nulla magna ad laboris laborum ullamco est occaecat consectetur sunt. Amet pariatur anim nulla id eu dolor labore. Consequat laborum excepteur ut aliqua deserunt quis.\r\n",
          favoriteFruit: "strawberry",
        },
        {
          id: "6278f67c684b7dbefbc56843",
          picture:
            "https://www.zooplus.hu/magazin/wp-content/uploads/2021/05/devon-rex-768x512-1.jpg",
          age: 10,
          eyeColor: "blue",
          name: "Meghan Dejesus",
          gender: "female",
          species: "cat",
          breed: "devon rex",
          about:
            "Pariatur labore et dolor reprehenderit voluptate ut laborum consectetur anim occaecat eiusmod minim ad. Aliquip enim occaecat voluptate sunt culpa fugiat est tempor magna commodo excepteur. Occaecat ullamco commodo nisi do anim pariatur laborum excepteur ut nostrud. Duis ad laborum consectetur nostrud cillum exercitation laboris quis tempor elit. Lorem consequat ipsum ipsum nulla irure ullamco. Cillum consectetur in ut voluptate cillum excepteur aute. Ea pariatur aliqua consequat ullamco exercitation eu incididunt commodo quis.\r\n",
          favoriteFruit: "apple",
        },
        {
          id: "6278f67c6251c5b972c286c5",
          picture:
            "https://www.zooplus.hu/magazin/wp-content/uploads/2019/07/Border-Collie-1.jpg",
          age: 14,
          eyeColor: "green",
          name: "Ashley Livingston",
          gender: "male",
          species: "dog",
          breed: "border collie",
          about:
            "Enim excepteur incididunt non anim. Nulla eu aute id aute laborum commodo non consectetur commodo. Ut elit dolor aliqua ipsum. Consectetur consectetur laborum proident aliqua duis amet ut sint consectetur officia consectetur in do. Amet duis mollit minim proident duis fugiat esse.\r\n",
          favoriteFruit: "banana",
        },
        {
          id: "6278f67c302ffc8be8d468cd",
          picture:
            "https://www.purina-arabia.com/sites/default/files/2021-02/BREED%20Hero_0018_border_collie.jpg",
          age: 9,
          eyeColor: "blue",
          name: "Hendricks Barrera",
          gender: "male",
          species: "dog",
          breed: "border collie",
          about:
            "Minim ullamco officia aliqua eiusmod Lorem labore ea quis nostrud fugiat est. Esse eiusmod aute reprehenderit eu aliqua ut pariatur consectetur elit. Quis officia voluptate velit qui veniam quis deserunt cillum minim veniam.\r\n",
          favoriteFruit: "banana",
        },
        {
          id: "6278f67cf4a144c8862756ed",
          picture:
            "https://upload.wikimedia.org/wikipedia/commons/f/f0/Mops_oct09_cropped2.jpg",
          age: 7,
          eyeColor: "blue",
          name: "Clements Vargas",
          gender: "male",
          species: "dog",
          breed: "pug",
          about:
            "Esse occaecat reprehenderit pariatur veniam commodo amet dolor velit sit esse. Voluptate nulla minim quis aute nisi enim eu officia laboris exercitation. Occaecat incididunt nostrud incididunt dolore minim culpa eiusmod nisi occaecat officia id exercitation sint. Irure exercitation sit commodo pariatur. Sunt amet aliqua culpa ad voluptate laborum amet est fugiat aute esse.\r\n",
          favoriteFruit: "strawberry",
        },
        {
          id: "6278f67cbc0802507edf595b",
          picture:
            "https://thermaltake.azureedge.net/pub/media/catalog/product/cache/0b6cd258d732892ac0f7248ef9ed4204/l/2/l20m01.jpg",
          age: 1,
          eyeColor: "brown",
          name: "Huffman Johns",
          gender: "male",
          species: "rodent",
          breed: "mouse",
          about:
            "Reprehenderit fugiat ex nisi mollit incididunt ipsum. Et enim deserunt elit esse. Officia dolor veniam velit proident pariatur aute non eu culpa sint adipisicing quis dolor Lorem. Culpa excepteur anim veniam sint proident aliquip aute cillum sit duis. Cupidatat dolore elit tempor cillum id voluptate laborum elit aute. Id occaecat nostrud id ullamco magna veniam deserunt incididunt mollit ea laborum sunt sint in.\r\n",
          favoriteFruit: "strawberry",
        },
        {
          id: "6278f67c39cf5be3e3461bf8",
          picture:
            "https://assets.petco.com/petco/image/upload/f_auto,q_auto/905909-Center-1",
          age: 2,
          eyeColor: "green",
          name: "Chan Kirby",
          gender: "male",
          species: "rodent",
          breed: "hamster",
          about:
            "Minim aliqua consequat fugiat ullamco culpa aliqua excepteur culpa non. Irure anim non officia magna duis dolor laborum. Do cillum voluptate quis consequat irure deserunt Lorem cillum nostrud magna. Non dolore velit enim ullamco proident qui.\r\n",
          favoriteFruit: "banana",
        },
        {
          id: "6278f67cd83a269cad6c0b40",
          picture:
            "https://assets.petco.com/petco/image/upload/f_auto,q_auto/3346154-center-10",
          age: 3,
          eyeColor: "green",
          name: "Janet Conley",
          gender: "female",
          species: "rodent",
          breed: "guinea pig",
          about:
            "Amet veniam cupidatat ut magna aliqua pariatur Lorem id. Do laboris consectetur cillum mollit occaecat irure. Dolor elit labore fugiat pariatur fugiat labore. Aliqua ea esse non pariatur aliqua pariatur id et pariatur quis sint adipisicing voluptate sunt. Commodo deserunt veniam labore Lorem consectetur mollit id ea cupidatat sint quis. Commodo nostrud voluptate velit eiusmod pariatur ea. Magna irure anim labore minim fugiat cillum non adipisicing culpa labore.\r\n",
          favoriteFruit: "strawberry",
        },
      ],
      editOrAddAnimalVisible: false,
      selectedAnimal: null,
    };
  },
  methods: {
    animalDeleteClicked(animal) {
      this.animals = this.animals.filter((item) => item.id !== animal.id);
    },

    animalEditClicked(animal) {
      this.selectedAnimal = animal;
      this.editOrAddAnimalVisible = true;
    },

    hasItem(animalId) {
      return this.animals.find((x) => x.id === animalId);
    },

    animalAdded(animal) {
      if (this.hasItem(animal.id)) {
        this.animals = this.animals.map((item) => {
          if (item.id === animal.id) {
            return animal;
          } else {
            return item;
          }
        });
        this.editOrAddAnimalVisible = false;
      } else {
        this.animals.push(animal);
        this.editOrAddAnimalVisible = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
