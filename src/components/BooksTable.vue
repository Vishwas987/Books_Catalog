<template>
  <div class="container">
    <h3>List of All Books</h3>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">BookId</th>
          <th scope="col">Genre</th>
          <th scope="col">Price<a class="sort-by" @click="sortByPrice"></a></th>
          <th scope="col">Examine</th>
        </tr>
      </thead>
      <tbody>
        <tr class="table-raw" v-for="book in bookList" :key="book.bookId" @click="openDetails(book)">
            <td>{{book.bookId}}</td>
            <td>{{book.genre}}</td>
            <td>{{book.price}}</td>
            <td>No</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import router from '../router';

    export default{
        name: 'BooksTable',
        setup(props, {emit}){

          function sortByPrice(){
              emit('sortByPrice-task');
          }
          function openDetails(book){
            router.push({
              name: 'Details',
              params: {book_s: JSON.stringify(book)}
            });
            
          }

          return {sortByPrice, openDetails};
        },
        props: {
            bookList: Array
        }
    }
</script>

<style scoped>
.container{
    margin-bottom:20px; 
}
.table-raw:hover{
  background-color: beige;
}
.sort-by { 
	padding-right: 18px;
	position: relative;
    cursor: pointer;
}
.sort-by:before, .sort-by:after {
	border: 4px solid transparent;
	content: "";
	display: block;
	height: 0;
	right: 5px;
	top: 50%;
	position: absolute;
	width: 0;
}
.sort-by:before {
	border-bottom-color: #666;
	margin-top: -9px;
}
.sort-by:after {
	border-top-color: #666;
	margin-top: 1px;
}
</style>
