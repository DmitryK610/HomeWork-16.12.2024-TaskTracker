<template>
  <div class=" user_info">
    <h1>Форма обратной связи</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="name"> Имя:</label>
        <input type="text" v-model="user.name" required />
      </div>
      <div>
        <label for="email"> Электронная почта:</label>
        <input type="text" v-model="user.email" required />
      </div>
      <div>
        <label for="age"> Возраст:</label>
        <input type="text" v-model="user.age" required />
      </div>
      <div>
        <label for="tel.number"> Номер телефона:</label>
        <input type="text" v-model="user.tel" required />
  
      </div>
      <button type="submit">Подтвердить</button>
    </form>
    <div v-if="submitted">
      <h2>Полученная информация</h2>
      <p>Имя : {{ user.name }}</p>
      <p>Эл. почта : {{ user.email }}</p>
      <p>Возраст : {{ user.age }}</p>
      <p>Номер телефона : {{ user.tel }}</p>
    </div>
  </div>
</template>
<script lang="ts">


import { defineComponent, ref } from 'vue'
export default defineComponent({
  name: 'userForm',
  setup() {
    const user = ref({
      name: '',
      email: '',
      tel: null as number | null,
      age: null as number | null, //допускает пустое поле без значения
    }) 
    const submitted = ref(false) 
    const submitForm = () => {
      submitted.value = true
    }
    return {  //пишется то что должо быт в контексте в шаблоне
      user,
      submitted,
      submitForm,
    }
  },
});
</script>
