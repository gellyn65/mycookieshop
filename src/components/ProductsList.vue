<template>
    <div class="product-container">
      <h2>Products</h2>
      <div class="product-list-container">
        <ul class="product-list">
          <li v-for="product in products" :key="product.id" class="product-item">
            <div class="product-info">
              <span>{{ product.name }} - ₱{{ product.price }}</span>
            </div>
            <button @click="addToCart(product)" class="add-to-cart-btn">Add to Cart</button>
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductsList',
    props: {
      products: {
        type: Array,
        required: true
      }
    },
    methods: {
      addToCart(product) {
        this.$emit('add-to-cart', product);
      }
    }
  };
  </script>
  
  <style scoped>
  .product-container {
    text-align: center; /* Center the content horizontally */
  }
  
  .product-list-container {
    padding: 20px; /* Add padding to the container */
    border: 1px solid #ccc; /* Add border around the container */
    border-radius: 8px; /* Add border radius */
    display: inline-block; /* Ensure the container wraps around the list */
    width: calc(100% - 40px); /* Adjust width to accommodate padding */
    overflow: auto; /* Add overflow for horizontal scrolling */
  }
  
  .product-list {
    list-style-type: none; /* Remove default list styles */
    padding: 0; /* Remove default padding */
    margin: 0; /* Remove default margin */
    display: flex; /* Use flexbox for layout */
    flex-wrap: wrap; /* Allow wrapping */
    justify-content: space-between; /* Distribute items evenly */
  }
  
  .product-item {
    margin-bottom: 20px; /* Add margin between items */
    border: 1px solid #ccc; /* Add border */
    padding: 10px; /* Add padding */
    background-color: #f9f9f9; /* Background color for each item */
    border-radius: 8px; /* Add border radius */
    width: calc(20% - 24px); /* Set width for 5 products per row with margins */
    max-width: 200px; /* Limit maximum width */
  }
  
  .product-info {
    text-align: left;
  }
  
  .add-to-cart-btn {
    background-color: #bc833d; /* Green */
    border: none;
    color: white;
    padding: 8px 16px;
    width: 100%; /* Occupy full width */
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 15px;
    margin-top: 10px; /* Add margin to separate button */
    transition-duration: 0.4s;
    cursor: pointer;
  }
  
  .add-to-cart-btn:hover {
    background-color:#c99d66 ; /* Darker Green */
  }
  </style>
  