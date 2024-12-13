
<script>
    export default {
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

                bookPriceStyle: {
                    'padding': '5px',
                    'background': 'green',
                    'font-weight': '600',
                    'color': 'white',
                    'font-size': '1.5em',
                    'position': 'absolute',
                    'top': '0.25em',
                    'left': '0.25em',
                },

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
    <div class="book-container" :class="`book-container-${rowCount}-column`">
        <div class="book-item" :style="productCardStyle" v-for="(book, index) in books" :key="index" :class="{ 'first' : index === 0 }">
            <div class="book-image-area">
                <img v-bind:src="book.imageSrc">
                <span :style="bookPriceStyle">{{ book.price }}</span>
                <span class="sold-out-badge" v-show="book.stockAmount < 10">Almost sold out!</span>
            </div>
            <h2 v-bind:style="styleH2Title">{{ book.name }}
            </h2>
            <div>{{ book.desc }}</div>
            <button v-if="!book.isBasket" class="add-basket" @click="addBasket(book)">Add Basket</button>
        </div>
    </div>

</template>

<!-- v-model creates a two-way binding between an HTML control and the associated data. -->
<!-- v-bind creates a one-way binding. So any changes the user makes in the form aren't stored in state-->

<style scoped>
    .book-container {
        display: grid;
        grid-gap: 0.5em;
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
    .book-item {
        padding: 10px;
        border-radius: 5px;
    }
    .book-item img {
        width: 100%;
    }
    .book-item.first {
        background: grey;
        color:#fff;
    }
    .book-item.first h2 {
        color: #fff!important;
    }
    .book-image-area {
        position: relative;
    }
    .add-basket {
        font-size: 0.7em;
        color: black;
        float: right;
        text-align: center;
        cursor: pointer;
        margin: 5px 0;
    }
    .sold-out-badge {
        left:calc(100% - 95%);
        width: 80%;
        position: absolute;
        bottom: 0;
        background:red;
        padding: 5px;
        color: white;
        border-radius: 5px;
    }
</style>