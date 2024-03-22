<template>
  <div id="app">
    <h1>Sweet Cookies Shopping Cart</h1>
    <ProductsList :products="products" @add-to-cart="addToCart" />
    <ShopCart :cart="cart" @update-quantity="updateQuantity" @remove-item="removeItem" />
  </div>
</template>

<script>
import ProductsList from './components/ProductsList.vue';
import ShopCart from './components/ShopCart.vue';


// import ShopCart from './components/ShopCart.vue';

export default {
  name: 'App',
  components: {
    ProductsList,
    ShopCart

  },
  data() {
    return {
      products: [
        { id: 1, name: 'Chocolate Chip', price: 150, },
        { id: 2, name: 'Oatmeal Raisin', price: 200, },
        { id: 3, name: 'Peanut Butter ', price: 200, },
        { id: 4, name: 'Macadamia Nut', price: 250, },
        { id: 5, name: 'Crinkles', price: 130, },
        { id: 6, name: 'Red Velvet', price: 170, },
        { id: 7, name: 'Almond Cookie', price: 250, },
        { id: 8, name: 'Double Chocolate', price: 250, },
        { id: 9, name: 'Macaroons', price: 250, },
        { id: 10, name: 'Gingerbread', price: 200, },
        // Add more products as needed
      ],
      cart: []
    };
  },
  methods: {
    addToCart(product) {
      const existingItem = this.cart.find(item => item.id === product.id);
      if (existingItem) {
        existingItem.quantity++;
      } else {
        this.cart.push({ ...product, quantity: 1 });
      }
    },
    updateQuantity(itemId, newQuantity) {
      const item = this.cart.find(item => item.id === itemId);
      if (item) {
        item.quantity = newQuantity;
      }
    },
    removeItem(itemId) {
      this.cart = this.cart.filter(item => item.id !== itemId);
    }
  }
};
</script>

<style>
.h1{
  text-align: center;
}
</style>

