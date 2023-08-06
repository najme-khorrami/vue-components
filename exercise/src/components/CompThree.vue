<template>
    <h2>Component Three</h2>
    <form @submit.prevent="addItem">
        <div class="box">
            <label>What do you need?<br>
                <input type="text" v-model="itemName" placeholder="item name.." required>
            </label>
        </div>
        <div class="box">
            <label>How many?<br>
                <input type="number" v-model="itemNumber" placeholder="number of items.." required>
            </label>
        </div>
        <div class="box">
            <label>Important?
                <input type="checkbox" v-model="itemImportant">{{ itemImportant }}
            </label>
        </div>
        <button type="submit">add to list</button>
        <hr>
        <div>
            <h3>Shopping List</h3>
            <ul id="notFound">
                <li v-for="x in shoppingList" v-show="!x.found" :class="{impClass:x.important}" @click="x.found=!x.found">{{ x.name }} , {{ x.number }}</li>
            </ul>
            <ul id="found">
                <li v-for="x in shoppingList" v-show="x.found" @click="x.found=!x.found">{{ x.name }} , {{ x.number }}</li>
            </ul>
        </div>
    </form>
</template>
<script>
    export default {
        data() {
            return {
                itemName: '',
                itemNumber: '',
                itemImportant: false,
                shoppingList: [
                    { name: 'Tomatoes', number: 5, important: false, found: false },
                    { name: 'Bread', number: 1, important: false, found: false },
                    { name: 'Soap', number: 1, important: true, found: true }
                ]
            }

        },
        methods: {
            addItem() {
                let item = {
                    name: this.itemName,
                    number: this.itemNumber,
                    important: this.itemImportant,
                    found: false
                }
                this.shoppingList.push(item)
                this.itemName='',
                this.itemNumber='',
                this.itemImportant=false
            }
        }
    }
</script>
<style scoped>
    ul {
        list-style-type: none;
    }
    .box{
        margin: 10px 0;
    }
    #notFound li {
        background-color: lightgreen;
    }
    #found li {
        background-color: lightgray;
        text-decoration: line-through;
    }
    li {
        padding: 5px;
        border-radius: 8px;
        margin: 2px 0;
    }
    .impClass {
        background-color: lightpink !important;
    }
</style>