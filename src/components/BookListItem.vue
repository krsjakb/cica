<template>
  <div class="col-8 offset-2 mt-2 mb-2">
    <b-card-group deck>
      <b-card bg-variant="light" :header="book.title" class="text-center">
        <b-card-text>
          <p><strong>Author:</strong> {{ book.author }}</p>
          <p><strong>Description:</strong> {{ book.description }}</p>
          <p><strong>Price:</strong> {{ book.price }}$</p>
        </b-card-text>
        <b-button variant="danger" @click="deleteClicked">Delete</b-button>
      </b-card>
    </b-card-group>
  </div>
</template>

<script>
export default {
  name: "BookListItem",
  props: {
    book: {
      type: Object,
      required: true,
    },
  },
  methods: {
    deleteClicked() {
      this.$emit("deleteClicked", this.book);
    },
  },
};
</script>

<style lang="scss" scoped></style>
