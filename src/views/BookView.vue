<template>
  <div>
    <div v-for="(bookItem, index) in books" :key="'book-item' + index">
      <book-list-item :book="bookItem" @deleteClicked="bookDeleteClicked" />
    </div>
  </div>
</template>

<script>
import BookListItem from "../components/BookListItem.vue";

export default {
  name: "BookView",
  components: {
    BookListItem,
  },
  data() {
    return {
      books: [
        {
          title: "Test1",
          author: "Test1 Author",
          description: "Test1 Description",
          price: 30,
        },
        {
          title: "Test2",
          author: "Test2 Author",
          description: "Test2 Description",
          price: 20,
        },
        {
          title: "Test3",
          author: "Test3 Author",
          description: "Test3 Description",
          price: 10,
        },
      ],
    };
  },
  methods: {
    bookDeleteClicked(book) {
      this.books = this.books.filter((item) => item !== book);
    },
  },
};
</script>

<style lang="scss" scoped></style>
