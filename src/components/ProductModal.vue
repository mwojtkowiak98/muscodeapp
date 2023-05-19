<template>
    <div id="modalWrapper">
        <div id="modalElement">
            <h2>Edycja produktu: {{product.name}}</h2>
            <div id="imageWrapper">
                <img :src="product.photo" alt="Product image">
            </div>
            <div id="labelWrapper">
                <label for="name">Nazwa produktu:</label>
                <input type="text" id="name" v-model="modalProductDetails.name">

                <label for="price">Cena:</label>
                <input type="number" id="price" v-model="modalProductDetails.price">

                <label for="discountPrice">Cena promocyjna:</label>
                <input type="number" id="discountPrice" v-model="modalProductDetails.discountPrice">

                <label for="currency">Waluta:</label>
                <select name="currency" id="currency" v-model="modalProductDetails.currency">
                    <option value="$">$</option>
                    <option value="PLN">PLN</option>
                    <option value="EUR">EUR</option>
                </select>
            </div>
            <div id="buttonWrapper">
                <button @click="saveChanges">Zapisz</button>
                <button @click="discardChanges">Anuluj</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        product: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            modalProductDetails: {...this.product},
        }
    },
    methods: {
        saveChanges() {
            this.$emit('updateProduct', this.modalProductDetails)
        },
        discardChanges() {
            this.$emit('discardChanges')
        }
    }
}
</script>

<style scoped>
#modalWrapper {
    position: absolute !important;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
    left: 0px;
    top: 0px;
    padding: 0px;
    cursor: default !important;
}
#modalElement {
    height: 100%;
    width: 594px;
    background: white;
    margin-left: auto;
    box-shadow: 0px 0px 25px 0px rgba(80, 80, 80, 1);
    cursor: default;
}
h2 {
    padding-top: 18px;
    padding-bottom: 18px;
    padding-left: 12px;
    font-size: 20px;
    border-bottom: 4px solid #343e87;
    color: #333;
}
#imageWrapper {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    overflow: hidden;
    display: flex;
    justify-content: center;
    margin: 32px auto 16px auto;
    box-shadow: 0px 0px 8px 0px #b2b2b2;
}
img {
    object-fit: scale-down;
}
#labelWrapper {
    display: flex;
    flex-direction: column;
    padding: 0px 12px;
}
input, select {
    color: #384a5c;
    border: none;
    border-bottom: 1px solid #b2b2b2;
    padding: 8px 0px 4px 0px;
}
label {
    margin-top: 14px;
    color: #776d6d;
}
#labelWrapper > label:first-child {
    margin-top: 0px;
}
#buttonWrapper {
    position: absolute;
    bottom: 0px;
    padding: 12px;
    border-top: 1px solid #b2b2b2;
    width: -webkit-fill-available;
}
#buttonWrapper > button:hover, select:hover, select > option:hover {
    cursor: pointer;
}
#buttonWrapper > button:last-child {
    color: #384c5a;
    border: 1px solid #b2b2b2;
    background: white;
    padding: 6px 12px;
}
#buttonWrapper > button:first-child {
    color: white;
    border: 1px solid #b2b2b2;
    background: #862583;
    padding: 6px 12px;
    margin-right: 6px;
}
label, input {
    padding-left: 2px;
}
</style>