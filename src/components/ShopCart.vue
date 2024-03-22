<template>
    <div class="cart-container">
      <h2>Shopping Cart</h2>
      <ul class="cart-list">
        <li v-for="item in cart" :key="item.id">
          <div class="cart-item">
            <div>
              <span>{{ item.name }} - ₱{{ item.price }}</span>
              <br>
              <span>Quantity: </span>
              <input type="number" v-model="item.quantity" @input="updateQuantity(item.id, $event.target.value)">
            </div>
            <button @click="removeItem(item.id)" class="remove-btn">Remove</button>
          </div>
        </li>
      </ul>
      <p class="total"><b>Total:</b> ₱{{ total }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ShoppingCart',
    props: {
      cart: {
        type: Array,
        required: true
      }
    },
    computed: {
      total() {
        return this.cart.reduce((total, item) => total + (item.price * item.quantity), 0);
      }
    },
    methods: {
      updateQuantity(itemId, newQuantity) {
        this.$emit('update-quantity', itemId, newQuantity);
      },
      removeItem(itemId) {
        this.$emit('remove-item', itemId);
      }
    }
  };
  </script>
  
  <style scoped>
  .cart-container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .h2{
    text-align: center;
  }
  
  .cart-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .remove-btn {
    background-color: #dc3545; /* Red */
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 3px;
    cursor: pointer;
    font-size: 12px;
    margin-top: 23px; /* Adjusted margin */
  }
  
  .remove-btn:hover {
    background-color: #bd2130; /* Darker Red */
  }
  
  .cart-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 10px;
    padding: 15px 10px;
    border-bottom: 1px solid #ece7e7;
    
  }
  
  .cart-item input[type="number"] {
    margin-top: 5px; /* Adjusted margin */
  }
  
  .total {
    text-align: center;
    margin-top: 20px;
    font-weight: bold; /* Bold font for total */
  }
  </style>
  