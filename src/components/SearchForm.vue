<template>
    <form>
        <div id="div-search-id" class="container pt-2">
            <h3>Search Book By Id</h3>
            <form action="#">
                <input type="text" v-model="inputId" class="form-control">
                <button @click="searchById" class="btn" type="submit">Search Product</button>
            </form> 
        </div>

        <div id="div-search-genre" class="container pt-2">
            <h3>Search Book By Genre</h3>
            <form action="#">
                <input type="text" v-model="inputGenre" class="form-control">
                <button @click="searchByGenre" class="btn" type="submit">Search Genre</button>
            </form>
        </div>

        <div id="div-search-price" class="container pt-2">
            <h3>Search Book By Price</h3>
            <form action="#">
                <input type="text" v-model="inputPrice" class="form-control">
                <button @click="searchByPrice" class="btn" type="submit">Search Price</button>
            </form>
        </div>
    </form>
</template>

<script>
    import { ref } from 'vue';
    export default{
        name: 'SearchForm',
        setup(props, {emit}){
            let inputId = ref('');
            let inputPrice = ref('');
            let inputGenre = ref('');

            function searchByPrice(e){
                e.preventDefault();
                if(inputPrice.value.length <= 0)return;

                const price = parseInt(inputPrice.value);

                emit('searchPrice-task', price);
            }

            function searchById(e){
                e.preventDefault();
                if(inputId.value.length <= 0)return;

                const id = parseInt(inputId.value);

                emit('searchId-task', id);
            }

            function searchByGenre(e){
                e.preventDefault();
                if(inputGenre.value.length <= 0)return;

                emit('searchGenre-task', inputGenre.value);
            }

            return {inputId, inputPrice, inputGenre, searchByGenre, searchById, searchByPrice};
        },
    }
</script>

<style scoped>
.pt-2{
    padding-top:20px;
}

.container{
    margin-bottom:20px; 
}

.form-control{
    width:25%;
    display:inline;
}
</style>
