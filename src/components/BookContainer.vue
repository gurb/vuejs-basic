
<script>
    import BookItem from '/src/components/BookItem.vue'

    export default {
        name: 'BookContainer',
        components: {
            BookItem,
        },

        props: {
            bookItems: {
                type: Array,
            },
        },

        data() {
            return {
                rowCount: "8",
            };
        },
        
        methods: {
            addBasket(book){
                // book.isBasket = !book.isBasket;
                // this.basketCount = this.books.filter(x => x.isBasket).length;
            },

            clearBasket () {
                // this.books.map(x => x.isBasket = 0);
                // this.basketCount = 0;
            }
        },
        computed: {
            books() {
                return this.bookItems;
            }
        }
    }
</script>

<template>
    <div class="book-item" v-for="(book, index) in bookItems" :key="index" :class="{ 'first' : index === 0 }">
        <book-item :bookItem="book"></book-item>
    </div>
</template>

<style scoped>
   
    
</style>