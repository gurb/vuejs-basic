<script>
    export default {
        name: 'BookItem',
        props: {
            bookItem: {
                name: String,
                desc: String,
                imageSrc: String,
                price: String,
                isBasket: Boolean,
                stockAmount: Number,
            }
        },
        data() {
            return {
                styleH2Title: {
                    'color': 'grey'
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
            }
        }
    }
</script>

<template>
    <div class="book-image-area">
        <img v-bind:src="bookItem.imageSrc">
        <span :style="bookPriceStyle">{{ bookItem.price }}</span>
        <span class="sold-out-badge" v-show="bookItem.stockAmount < 10">Almost sold out!</span>
    </div>
    <h2 v-bind:style="styleH2Title">{{ bookItem.name }}
    </h2>
    <div>{{ bookItem.desc }}</div>
    <button v-if="!bookItem.isBasket" class="add-basket" @click="addBasket(bookItem)">Add Basket</button>
</template>


<style>
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