<template>
    <div class="container">
    <h2>Book Details</h2>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">BookId</th>
          <th scope="col">Genre</th>
          <th scope="col">Price</th>
          <th scope="col">Examine</th>
        </tr>
      </thead>
      <tbody>
        <tr>
            <td>{{bookObj.bookId}}</td>
            <td>{{bookObj.genre}}</td>
            <td>{{bookObj.price}}</td>
            <td>No</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { reactive } from 'vue';

export default{
    name: 'BookDetails',
    props: ['book'],
    setup(){
        const bookObj = reactive({});

        return {bookObj};
    },
    created(){
        this.bookObj = JSON.parse(this.book);
    }
}
</script>

<style scoped>
.container{
    margin-bottom:20px; 
}
.table{
    border: 2px solid darkgrey;
}
</style>
