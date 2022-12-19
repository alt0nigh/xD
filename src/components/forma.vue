<template>
    <div id="forma">
        <form id="form" @submit.prevent="addProduct()">
            <input type="text" name="name" placeholder="Название товара"
             v-model="name"
             >
            <input type="date" name="date" placeholder="Дата приема товара"
             v-model="date"
             >
            <input type="number" name="amount" placeholder="Количество товара"
             v-model="amount"
             >
            <input type="number" name="price" placeholder="Цена за товар"
            v-model="price"
            >
            <button type="submit" class="button">Добавить</button>
        </form>
        <error v-if="isValidationNeed"/>
    </div>
</template>

<script>

import error from '@/components/error.vue'


export default {
    components: {
        error,
    },

    data() {
        return {
            name: null,
            date: null,
            amount: null,
            price: null,

            products: [],
            isErrorNeed: false
        }
    },
    methods: {
        addProduct() {

            const unmutatedProductsArray = [...this.products];

            let id = unmutatedProductsArray.length + 1;
            let name = this.name;
            let date = this.date;
            let amount = this.amount;
            let price = this.price;
            let eventualPrice = price * amount;

            const arr = [id, name, date, amount, price, eventualPrice];

            for(let el of arr) 
                if(!el) {
                    this.isValidationNeed = true;
                    return;
                };

                this.isValidationNeed = false;
            
            for(let product of this.products) 
                if(product.name === name) {
                    this.isValidationNeed = true;
                    return;
                };

            unmutatedProductsArray.push({
                    id,
                    name,
                    date,
                    amount,
                    price, 
                    eventualPrice
                });

            this.products = unmutatedProductsArray;
            this.$emit('getProducts', this.products);
        }
    },
    mounted() {
    }

}
</script>

<style scoped>

    #forma {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        padding-left: 20px; 
    }

    #form {
        display: flex;
        align-items: center;
        flex-direction: column;
        justify-content: center; 
        border: 3px solid rgba(31, 124, 36, 0.7);
        padding: 50px;
    }

    input {
        display: block;
        padding: 15px 70px;
        border: none;
        background-color: rgba(31, 124, 43, 0.7);
        color: #fff;
    }

    input[type="date"] {
        padding: 15px 98px;
    }

    input::placeholder {
        text-align: center;
        color: #fff;
        font-family: 'Montserrat', sans-serif;
        font-weight: 400;
    }

    input:hover {
        transition: ease .4s;
        border: 1px solid #000;
    }

    input:not(:last-child) {
        margin-bottom: 20px;
    }

    .button {
        border: none;
        background-color: rgba(24, 85, 22, 0.8);
        padding: 15px 40px;
        border-radius: 5px;
        color: #fff;
    }

    .button:hover {
        border-radius: 30px;
        border: 1px solid #000;
        transition: ease .5s;
    }

</style>