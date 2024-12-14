<script>
    import BookContainer from '/src/components/BookContainer.vue';

    export default {
        // vue.js will convert the component named MainPage into the kebab-cased main-page. (example: <main-page/>)
        name: 'MainPage',
        components: {
            BookContainer,
        }, 
        // props: [
            // 'property1', 
            // 'property2',
        // ]
        // provide more robust information about the props by defining a schema.
        props: {
            property3: String,
            property4: Number
        },
        data() {
            return {
                styleH2Title: {
                    'color': 'grey'
                },

                productCardStyle: {
                    
                },

                rowCount: "8",
                basketCount: 0,

                rowCountList: [
                    {
                        value: "3",
                        label: "3-col"
                    },
                    {
                        value: "4",
                        label: "4-col"
                    },
                    {
                        value: "6",
                        label: "6-col"
                    },
                    {
                        value: "8",
                        label: "8-col"
                    }
                ],

                

                books: [
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$4.5',
                        isBasket: false,
                        stockAmount: 45,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$5.0',
                        isBasket: false,
                        stockAmount: 123,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$5.5',
                        isBasket: false,
                        stockAmount: 6,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 33,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 67,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 3,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 43,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 54,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 23,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 23,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 9,
                    },
                    {
                        name: 'Foundation',
                        desc: 'a cycle of five interrelated short stories',
                        imageSrc: './src/assets/images/foundation.jpg',
                        price: '$7.0',
                        isBasket: false,
                        stockAmount: 5,
                    }
                ]
            }
        },

        methods: {
            addBasket(book){
                book.isBasket = !book.isBasket;
                this.basketCount = this.books.filter(x => x.isBasket).length;
            },

            clearBasket () {
                this.books.map(x => x.isBasket = 0);
                this.basketCount = 0;
            }
        },

        computed: {
            // computed property
            getBasketList() {
                return this.books.filter(x => x.isBasket);
            }
        }
    }
</script>

<template>
    <div class="book-grid-control-container">
        <select v-model="rowCount">
            <!-- <option v-for="(stringItem, index) in rowCountList" :value="stringItem">
                {{ stringItem }}
            </option> -->
            <!-- Create a message to select one -->
            <option disabled value="">Select row status</option>
            <!-- Use v-for to create the list of options -->
            <option v-for="item in rowCountList" :value="item.value">
                {{ item.label }}
            </option>
        </select>
        <div class="basket-count-area">
            Basket: {{ basketCount }}
        </div>
        <button type="button" @click="clearBasket">
            Clear Basket
        </button>
    </div>
    <div class="main-page">
        <div class="book-container" :class="`book-container-${rowCount}-column`">
            <book-container :bookItems=books></book-container>
        </div>
        <div class="book-basket">
            <h3>Basket list</h3>
            <ul>
                <li v-for="item in getBasketList">{{ item.name }}</li>
            </ul>
        </div>
    </div>
    

</template>

<!-- v-model creates a two-way binding between an HTML control and the associated data. -->
<!-- v-bind creates a one-way binding. So any changes the user makes in the form aren't stored in state-->

<style scoped>
    .main-page {
        display:flex;
        column-gap: 2%;
        width: 100%;
    }
    .book-basket {
        width: 20%;
    }
    .book-container {
        width:80%;
        display: grid;
    }
    .book-container-3-column {
        grid-template-columns: repeat(3, 1fr);
    }
    .book-container-4-column {
        grid-template-columns: repeat(4, 1fr);
    }
    .book-container-6-column {
        grid-template-columns: repeat(6, 1fr);
    }
    .book-container-8-column {
        grid-template-columns: repeat(8, 1fr);
    }
    
</style>