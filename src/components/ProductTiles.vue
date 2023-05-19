<template>
    <div id="grid-item-3">
        <div v-for="product in products" :key="product.id" @click="openModal(product)">
            <div id="discountPercentageTag" v-if="product.discountPrice != null & product.discountPrice != ''">
                <span>{{discountPercentageCalc(product.price, product.discountPrice)}}%</span>
            </div>
            <h2>{{product.name}}</h2>
            <img id="product-image" :src="product.photo" alt="Product image">
            <div v-if="product.discountPrice != null & product.discountPrice != ''" id="doublePriceWrapper" >
                <span class="currentPrice">{{product.discountPrice}} {{product.currency}}</span>
                <span id="oldPrice">{{product.price}} {{product.currency}}</span>
            </div>
            <span class="currentPrice" v-else>{{product.price}} {{product.currency}}</span>
        </div>
        <productModal v-if="productClicked" :product="productDetails" @updateProduct="changeProductDetails" @discardChanges="discardModalChanges"/>
    </div>
</template>

<script>
import products from '@/assets/products'
import productModal from './ProductModal.vue'
export default {
    data() {
        return {
            products: products,
            productClicked: false,
            productDetails: null
        }
    },
    components: {
        productModal
    },
    methods: {
        openModal(product) {
            this.productClicked = true,
            this.productDetails = product
        },
        changeProductDetails(modalProductDetails) {
            Object.assign(this.productDetails, modalProductDetails)
            this.productClicked = false
        },
        discardModalChanges() {
            this.productClicked = false
        },
        discountPercentageCalc(price, discountPrice) {
            var percentage = Math.round(((discountPrice / price) * 100) - 100)
            return percentage
        }
    }
}
</script>

<style scoped>
#product-image {
    width: 100%;
    max-height: 200px;
    height: 100%;
    object-fit: contain;
    margin-bottom: 14px;
}
#grid-item-3 {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 15px;
}
h2 {
    margin-bottom: 14px;
}
#oldPrice {
    text-decoration: line-through;
    padding-top: 4px;
}
#doublePriceWrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-bottom: 2px;
}
.currentPrice {
    font-size: 16px;
    font-weight: bold;
    display: flex;
    justify-content: center;
    color: #862583;
}
#grid-item-3 > div:hover {
    cursor: pointer;
}
#discountPercentageTag {
    width: 180px;
    height: 200px;
    border-top: 20px solid #000;
    border-right: 20px solid transparent;
    transform: rotate(45deg);
    position: absolute;
    text-align: center;
    top: 2px;
    right: 2px;
}
#grid-item-3 > div {
    position: relative;
    overflow: hidden;
}
#discountPercentageTag > span {
    position: relative;
    top: -18px;
    color: #fff;
}
</style>