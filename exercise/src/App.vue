<template>
  <h2>Choose a component number:</h2>
  <div class="which-comp">
    <input type="radio" v-model="compName" :value="'comp-one'">one
    <input type="radio" v-model="compName" :value="'comp-two'">two
    <input type="radio" v-model="compName" :value="'comp-three'">three
  </div>
  <div class="container">

    <div class="box">
      <KeepAlive>
        <component :is="compName"></component>
      </KeepAlive>
    </div>

    <!-- <div class="box">
      <comp-one/>
    </div>
    <div class="box">
      <comp-two/>
    </div>
    <div class="box">
      <comp-three/>
    </div> -->
  </div>
</template>

<script>
  export default {
    data() {
      return {
        compName: 'comp-one'
      }
    }
  }
</script>

<style scoped>
  h2 {
    text-align: center;
    color: blue;
  }
  .which-comp {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 50px;
  }
  .which-comp input {
    margin-left: 20px;
  }
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .box {
    border: 2px dashed blue;
    padding: 10px;
    margin: 10px 0;
  }
</style>
