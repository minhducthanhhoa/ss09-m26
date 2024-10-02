<template>
    <div class="form-container">
      <h2>Thêm mới sản phẩm</h2>
      <form @submit.prevent="addProduct">
        <div class="form-group">
          <label for="productCode">Mã sản phẩm</label>
          <input type="text" v-model="product.productCode" id="productCode" />
        </div>
        <div class="form-group">
          <label for="productName">Tên sản phẩm</label>
          <input type="text" v-model="product.productName" id="productName" />
        </div>
        <div class="form-group">
          <label for="price">Giá</label>
          <input type="number" v-model="product.price" id="price" />
        </div>
        <div class="form-group">
          <label for="quantity">Số lượng</label>
          <input type="number" v-model="product.quantity" id="quantity" />
        </div>
        <button type="submit" class="submit-btn">Thêm mới</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { reactive } from 'vue'
  
  const product = reactive({
    productCode: '',
    productName: '',
    price: 0,
    quantity: 1
  })
  
  const addProduct = () => {
    console.log(product)
  }
  </script>
  
  <style scoped>
  .form-container {
    width: 300px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
  }
  
  h2 {
    text-align: center;
    font-size: 18px;
    margin-bottom: 20px;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  
  input {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .submit-btn {
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
  }
  
  .submit-btn:hover {
    background-color: #0056b3;
  }
  </style>
  