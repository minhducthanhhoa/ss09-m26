<template>
    <div class="register-container">
      <h2>Đăng ký tài khoản</h2>
      <form @submit.prevent="handleSubmit">
        <div>
          <label for="name">Tên sinh viên:</label>
          <input
            type="text"
            id="name"
            v-model="form.name"
            :class="{ 'is-invalid': errors.name }"
            required
            ref="nameInput"
          />
          <span v-if="errors.name" class="error">{{ errors.name }}</span>
        </div>
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
        <div>
          <label for="phone">Số điện thoại:</label>
          <input
            type="tel"
            id="phone"
            v-model="form.phone"
          />
        </div>
        <button type="submit">Đăng ký</button>
      </form>
      <p v-if="successMessage">{{ successMessage }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const form = ref({
    name: '',
    email: '',
    password: '',
    phone: '',
  });
  const errors = ref({
    name: '',
    email: '',
    password: '',
  });
  const successMessage = ref('');
  
  const validate = () => {
    errors.value.name = form.value.name ? '' : 'Tên sinh viên không được để trống';
    errors.value.email = form.value.email ? '' : 'Email không được để trống';
    errors.value.password = form.value.password ? '' : 'Mật khẩu không được để trống';
  
    const existingUsers = JSON.parse(localStorage.getItem('users')) || [];
    const emailExists = existingUsers.some(user => user.email === form.value.email);
    if (emailExists) {
      errors.value.email = 'Email đã tồn tại';
    }
  
    return !errors.value.name && !errors.value.email && !errors.value.password && !emailExists;
  };
  
  const handleSubmit = () => {
    if (validate()) {
      const existingUsers = JSON.parse(localStorage.getItem('users')) || [];
      existingUsers.push({
        name: form.value.name,
        email: form.value.email,
        password: form.value.password,
        phone: form.value.phone,
      });
      localStorage.setItem('users', JSON.stringify(existingUsers));
  
      successMessage.value = 'Đăng ký tài khoản thành công';
      resetForm();
      nextTick(() => {
        nameInput.value.focus();
      });
    }
  };
  
  const resetForm = () => {
    form.value.name = '';
    form.value.email = '';
    form.value.password = '';
    form.value.phone = '';
    errors.value = {};
  };
  </script>
  
  <style scoped>
  .register-container {
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