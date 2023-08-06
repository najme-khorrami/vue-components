<template>
    <h2>Component One</h2>
    <h3>The &lt;TransitionGroup&gt; Component</h3>
    <input type="text" v-model="inputVal" @keypress.enter="addItem">
    <button @click="addItem">add</button>
    <TransitionGroup name="liElems" tag="ul">
        <li v-for="x in list" :key="x">{{ x }}</li>
    </TransitionGroup>
</template>
<script>
    export default {
        data() {
            return {
                inputVal: '',
                list: ['one','two','three']
            }
        },
        methods: {
            addItem() {
                this.list.push(this.inputVal)
                this.inputVal = ''
            }
        }
    }
</script>

<style scoped>
    .liElems-enter-from {
        opacity: 0;
        rotate: 180deg;
    }
    .liElems-enter-to {
        opacity: 1;
        rotate: 0deg;
    }
    .liElems-enter-active {
        transition: all .5s;
    }
</style>