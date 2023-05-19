<template>
    <div id="grid-item-2">
        <h2>Lista Produktów</h2>
        <table>
            <thead>
                <tr>
                    <th>#</th>
                    <th>NAZWA</th>
                    <th>PROMOCYJNA CENA</th>
                    <th>CENA</th>
                    <th>WALUTA</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(product, index) in products" :key="product.id">
                    <td>{{index}}</td>
                    <td>{{product.name}}</td>
                    <td>{{product.discountPrice}}</td>
                    <td>{{product.price}}</td>
                    <td>{{product.currency}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import products from '@/assets/products'
export default{
    data() {
        return {
            products: products
        }
    }
}
</script>

<style scoped>
table {
    margin-top: 18px;
    width: 100%;
    border-collapse: collapse;
}
th {
    font-size: 12px;
    padding-bottom: 5px;
    text-align: left;
}
tr > td{
    padding: 5px 0px;
}
tr {
    border-bottom: 1px solid #b2b2b2;
}
tr > th:first-child {
    width: 8%;
    padding-left: 12px;
}
tr > th:nth-child(2) {
    width: 43%;
}
tr > th:nth-child(3) {
    width: 20%;
}
tr > th:nth-child(4) {
    width: 16%;
}
tr > td:first-child {
    padding-left: 12px;
}
tbody > tr:hover {
    background: #f5f8fa;
}
</style>
