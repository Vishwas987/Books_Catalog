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
        <tr :key="book.bookId" v-for="book in bookList">
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
    export default{
        name: 'BooksTable',
        props: {
            bookList: Array
        },
        methods: {
            sortByPrice(){
                this.$emit('sortByPrice-task');
            }
        }
    }
</script>

<style scoped>
.container{
    margin-bottom:20px; 
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
