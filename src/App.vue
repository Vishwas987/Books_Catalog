<script>
import SearchForm from './components/SearchForm.vue'
import BooksTable from './components/BooksTable.vue'

  export default{
    name: 'App',
    data(){
      return {
        bookList: [],
        bookListCurrent: [],
        isSorted: false
      }
    },
    components: {
      SearchForm,
      BooksTable
    },
    methods: {
      async fetchData(){
        const res = await fetch('/book_list.json');

        const data = await res.json();

        //Object.freeze(data);
        return data;
      },
      searchId(id){
        this.bookListCurrent = this.bookList.filter(book => book.bookId === id);
      },
      searchPrice(price){
        this.bookListCurrent = this.bookList.filter(book => book.price === price);
      },
      searchGenre(genre){
        genre = genre.toLowerCase();
        this.bookListCurrent = this.bookList.filter(book => book.genre.toLowerCase() === genre);
      },
      sortByPrice(){
        if(this.isSorted === false){
          this.bookListCurrent = this.bookListCurrent.sort((b1, b2) => b1.price - b2.price);
          this.isSorted = true;
        }
        else {
          this.bookListCurrent.reverse();
        }
      }
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
