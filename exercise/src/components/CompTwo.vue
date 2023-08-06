<template>
    <h2>Component TWo</h2>
    <form @submit.prevent="addItem">
        <p>
            <label>
                <input type="radio" required value="Dinner" v-model="itemType">Dinner
            </label>
            <label>
                <input type="radio" required value="Drink" v-model="itemType">Drink
            </label>
            <label>
                <input type="radio" required value="Dessert" v-model="itemType">Dessert
            </label>
        </p>
        <p v-show="itemType">
            <select required v-model="itemName" @change="newUrl">
                <option value="" selected disabled>Select item</option>
                <option v-for="x in preDefItems" :value="x.name" v-show="x.type===itemType" :data-url="x.imgUrl">{{ x.name }}</option>
            </select>
        </p>
        <img v-bind:src="itemUrl">
        <p v-show="itemName">
            <input type="number" placeholder="How many?" v-model="itemNumber" min-width="100px" required>
        </p>
        <button type="submit">Order</button>
    </form>
    <hr>
    <h3>Your Order:</h3>
    <ul>
      <li v-for="item in order">
          {{ item.name }}, {{ item.number}} <img v-bind:src="item.url">
      </li>
    </ul>
</template>

<script>
    export default {
        data() {
            return {
                itemName: '',
                itemType: '',
                itemUrl: '',
                itemNumber: null,
                preDefItems: [
                    { name: 'Burrito', type: 'Dinner', imgUrl: './assets/images/img_burrito.svg' },
                    { name: 'Pizza', type: 'Dinner', imgUrl: './assets/images/img_pizza.svg' },
                    { name: 'Pho Soup', type: 'Dinner', imgUrl: './assets/images/img_soup.svg' },
                    { name: 'Spaghetti', type: 'Dinner', imgUrl: './assets/images/img_spaghetti.svg' },
                    { name: 'Fish', type: 'Dinner', imgUrl: './assets/images/img_fish.svg' },
                    { name: 'Cake', type: 'Dessert', imgUrl: './assets/images/img_cake.svg' },
                    { name: 'Coke', type: 'Drink', imgUrl: './assets/images/img_soda.svg' },
                    { name: 'Green Soda', type: 'Drink', imgUrl: './assets/images/img_greenSoda.svg' },
                    { name: 'Doughnut', type: 'Dessert', imgUrl: './assets/images/img_doughnut.svg' },
                    { name: 'Lemonade', type: 'Drink', imgUrl: './assets/images/img_lemonade.svg' },
                    { name: 'Water', type: 'Drink', imgUrl: './assets/images/img_water.svg' }
                ],
                order: []
            }
        },
        methods: {
            addItem() {
                let item = {
                    name: this.itemName,
                    number: this.itemNumber,
                    url: this.itemUrl
                }
                this.order.push(item)
                this.itemType = ''
                this.itemName = ''
                this.itemNumber = null  
                this.itemUrl = ''
            },
            newUrl(e) {
                this.itemUrl = e.target.options[e.target.selectedIndex].getAttribute("data-url")
            }
        }
    }
</script>

<style scoped>
    p {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }
    form img {
      width: 50px;
    }
    ul{
        list-style-type: none;
    }
    li {
      margin: 2px;
      width: 150px;
      height: 35px;
      line-height: 35px;
      background-color: aquamarine;
      border-radius: 8px;
      padding: 2px 5px;
      text-align: center;
    }
    li img {
        height: 100%;
        float: right;
    }
</style>