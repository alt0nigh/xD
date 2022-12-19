<template>
    <div id="producti2">
        <div class="product" v-for="product in products" :key="product.id">
            <div class="products" id="id">
                <h2>Порядковый номер: {{product.id}}</h2>
            </div>
            <div class="products" id="name">
                <h2>Название продукта: {{product.name}}</h2>
            </div>
            <div class="products" id="date">
                <h2>Дата приема товара: {{product.date}}</h2>
            </div>
            <div class="products" id="amount">
                <h2>Количество продукта: {{product.amount}}</h2>
            </div>
            <div class="products" id="price">
                <h2>Цена за товар: {{product.price}}</h2>
            </div>
            <div class="products" id="price">
                <h2>Итоговая сумма: {{product.eventualPrice}}</h2>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        products: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>

#producti2 {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 40px 0;
}
.product {
    width: 70%;
}


.product:not(:last-child) {
    margin-bottom: 50px;
}

.products {
    padding: 20px 0 20px 10px;
}

.products:not(:first-child, :last-child) {
    border: 2px solid rgba(31, 124, 31, 0.7);
    border-top: none;
}

.products:nth-child(2) {
    border-top: 2px solid rgba(31, 124, 36, 0.7);
}
</style>