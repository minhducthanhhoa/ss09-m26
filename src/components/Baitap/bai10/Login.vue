<template>
    <div class="login-container">
      <h2>Đăng nhập tài khoản</h2>
      <form @submit.prevent="handleSubmit">
        <div>
          <label for="email">Email:</label>
          <input
            type="email"
            id="email"
            v-model="form.email"
            :class="{ 'is-invalid': errors.email }"
            required
          />
          <span v-if="errors.email" class="error">{{ errors.email }}</span>
        </div>
        <div>
          <label for="password">Mật khẩu:</label>
          <input
            type="password"
            id="password"
            v-model="form.password"
            :class="{ 'is-invalid': errors.password }"
            required
          />
          <span v-if="errors.password" class="error">{{ errors.password }}</span>
        </div>
        <button type="submit">Đăng nhập</button>
      </form>
      <p v-if="message">{{ message }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const form = ref({
    email: '',
    password: '',
  });
  const errors = ref({
    email: '',
    password: '',
  });
  const message = ref('');
  
  const validate = () => {
    errors.value.email = form.value.email ? '' : 'Email không được để trống';
    errors.value.password = form.value.password ? '' : 'Mật khẩu không được để trống';
    
    return !errors.value.email && !errors.value.password;
  };
  
  const handleSubmit = () => {
    if (validate()) {
      const existingUsers = JSON.parse(localStorage.getItem('users')) || [];
      const user = existingUsers.find(user => user.email === form.value.email && user.password === form.value.password);
  
      if (user) {
        message.value = 'Đăng nhập thành công';
      } else {
        message.value = 'Đăng nhập thất bại';
      }
    }
  };
  </script>
  
  <style scoped>
  .login-container {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9; /* Màu nền giống ảnh */
  }
  
  h2 {
    text-align: center;
  }
  
  input {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  button {
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  .error {
    color: red;
    font-size: 0.9em;
  }
  
  .is-invalid {
    border-color: red;
  }
  </style>