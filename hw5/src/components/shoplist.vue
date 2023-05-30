<template>
  <h1>請按照順序輸入ID</h1>
  <div id="app">
    <form v-on:submit.prevent="addItem">
      <p>
        ID?
        <input type="number" required placeholder="item ID.." v-model="itemId">
      </p>
      <p>
        Year?
        <input type="number" placeholder="Year of items.." v-model="itemYear">
      </p>
      <p>
        Price?
        <input type="number" placeholder="Price of items.." v-model="itemPrice">
      </p>
      <button type="submit">Submit</button>
    </form>

    <div>
      <h1>高筋麵粉價格資料(22kg)</h1>
      <table>
        <thead>
        <tr>
          <th>id</th>
          <th>year</th>
          <th>price</th>
        </tr>
        </thead>
      </table>
      <ul>
        <li v-for="item in shoppingList">{{ item.id }}, {{ item.year}}, {{ item.price}}</li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      itemID: null,
      itemYear: null,
      itemPrice: null,
      shoppingList: [
        { id: 1, year: 2023,  price:760}
      ]
    }
  },
  methods: {
    addItem(){
      let item = {
        id: this.itemId,
        year: this.itemYear,
        price: this.itemPrice
      }
      this.shoppingList.push(item)
      this.itemId = null
      this.itemYear = null
      this.itemPrice = null
    }
  }
}
</script>

<style scoped>
form {
  border: dashed black 1px;
  width: 200px;
  padding: 20px;
}
</style>