<script>
import SearchForm from './components/SearchForm.vue'
import BooksTable from './components/BooksTable.vue'
import { ref } from 'vue';

  export default{
    name: 'App',
    setup(){
      const bookList = ref([]);
      const bookListCurrent = ref([]);
      let isSorted = false;

      function searchId(id){
        bookListCurrent.value = bookList.value.filter(book => book.bookId === id);
      }
      function searchPrice(price){
        bookListCurrent.value = bookList.value.filter(book => book.price === price);
        isSorted = false;
      }
      function searchGenre(genre){
        genre = genre.toLowerCase();
        bookListCurrent.value = bookList.value.filter(book => book.genre.toLowerCase() === genre);
        isSorted = false;
      }
      function sortByPrice(){
        if(isSorted === false){
          bookListCurrent.value = bookListCurrent.value.sort((b1, b2) => b1.price - b2.price);
          isSorted = true;
        }
        else {
          bookListCurrent.value.reverse();
        }
      }

      return {bookList, bookListCurrent, isSorted, searchId, searchGenre, searchPrice, sortByPrice};
    },
    components: {
      SearchForm,
      BooksTable
    },
    methods: {
      async fetchData(){
        const res = await fetch('/book_list.json');

        const data = await res.json();

        return data;
      },
    },

    async created(){
      this.bookList = await this.fetchData();
      this.bookListCurrent = this.bookList;
    }
  }
</script>

<template>
  <main>
    <SearchForm @searchId-task="searchId" @searchPrice-task="searchPrice" @searchGenre-task="searchGenre" />
    <BooksTable :bookList="bookListCurrent" @sortByPrice-task="sortByPrice" />
  </main>
</template>

<style scoped>

</style>
