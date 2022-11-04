<template>
    <router-link class="back-btn" to="/">Go Back</router-link>
    <BookDetails :book="book_s" />
</template>

<script>
import BookDetails from '../components/BookDetails.vue';

export default{
    props: {
        book_s: String
    },
    components: {
        BookDetails
    }
}
</script>

<style scoped>
.back-btn{
    font-size: 1.5rem;
    text-decoration: underline;
}
</style>