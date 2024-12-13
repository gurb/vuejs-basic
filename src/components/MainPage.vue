
<script>
    export default {
        data() {
            return {
                styleH2Title: {
                    'color': 'grey'
                },

                productCardStyle: {
                    
                },

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
        }
    }
</script>

<template>
    <div class="book-container">
        <div class="book-item" :style="productCardStyle" v-for="(book, index) in books" :key="index" :class="{ 'first' : index === 0 }">
            <div class="book-image-area">
                <img v-bind:src="book.imageSrc">
                <span :style="bookPriceStyle">{{ book.price }}</span>
                <span class="sold-out-badge" v-show="book.stockAmount < 10">Almost sold out!</span>
            </div>
            <h2 v-bind:style="styleH2Title">{{ book.name }}
            </h2>
            <div>{{ book.desc }}</div>
            <button v-if="!book.isBasket" class="add-basket">Add Basket</button>
        </div>
    </div>

</template>

<style scoped>
    .book-container {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
        grid-gap: 0.5em;
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