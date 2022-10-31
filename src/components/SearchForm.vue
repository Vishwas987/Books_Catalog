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
    export default{
        name: 'SearchForm',
        data(){
            return {
                inputId: '',
                inputPrice: '',
                inputGenre: ''
            }
        },
        methods: {
            searchByPrice(e){
                e.preventDefault();
                if(this.inputPricelength <= 0)return;

                const price = parseInt(this.inputPrice);

                this.$emit('searchPrice-task', price);
            },

            searchById(e){
                e.preventDefault();
                if(this.inputId.length <= 0)return;

                const id = parseInt(this.inputId);

                this.$emit('searchId-task', id);
            },

            searchByGenre(e){
                e.preventDefault();
                if(this.inputGenre.length <= 0)return;

                this.$emit('searchGenre-task', this.inputGenre);
            }
        }
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
