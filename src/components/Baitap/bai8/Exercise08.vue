<template>
    <div class="form-container">
      <h2>Thêm mới tài khoản</h2>
      <form @submit.prevent="register">
        <div class="form-group">
          <label for="name">Họ và tên</label>
          <input type="text" v-model="user.name" id="name" />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input type="email" v-model="user.email" id="email" />
        </div>
        <div class="form-group">
          <label for="password">Mật khẩu</label>
          <input type="password" v-model="user.password" id="password" />
        </div>
        <div class="form-group">
          <label for="confirmPassword">Nhập lại mật khẩu</label>
          <input type="password" v-model="user.confirmPassword" id="confirmPassword" />
        </div>
        <button type="submit" class="submit-btn">Đăng ký</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { reactive } from 'vue'
  
  const user = reactive({
    name: '',
    email: '',
    password: '',
    confirmPassword: ''
  })
  
  const register = () => {
    console.log(user)
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
  