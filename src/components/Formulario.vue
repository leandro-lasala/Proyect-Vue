<template>
  <div class="container">
    <h1>Mi formulario</h1>
    <form @submit.prevent="enviarFormulario">
      <div class="campo">
        <label>Tu nombre:</label>
        <input 
          type="text"
          v-model="formulario.nombre" 
          placeholder="Tu nombre" 
        >
      </div>
      <div class="campo">
        <label>Email:</label>
        <input 
          type="email"
          v-model="formulario.email" 
          placeholder="email@gmail.com" 
        >

      </div>
      <div class="campo">
        <label>Mensaje:</label>
        <textarea 
          v-model="formulario.mensaje" 
          placeholder="Escribe tu mensaje" 
        ></textarea>
      </div>

      <button type="submit">Enviar</button>
    </form>

    <Transition name="fade">
      <div v-if="enviado" class="resultado">
        <h2>¡Formulario Exitoso!</h2>
        <p><strong>Nombre: </strong>{{formulario.nombre}}</p>
        <p><strong>Mail: </strong>{{formulario.email}}</p>
        <p><strong>Mensaje: </strong>{{formulario.mensaje}}</p>
      </div>
    </Transition>
  </div>  
</template>

<script setup>
import { ref } from 'vue'

const formulario = ref({
  nombre: '',
  email: '',
  mensaje: ''
});

const enviado = ref(false)

const enviarFormulario = ()=>{
  console.log("Formulario enviado");
  enviado.value = true

  setTimeout(()=>{
    enviado.value = false
    formulario.nombre = ''
    formulario.mail = ''
    formulario.mensaje = ''
  }, 3000)
}


</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 50px auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  color: #ffffff;
  text-align: center;
}

.campo {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 5px;
  font-weight: bold;
  color: #555;
}

input, textarea {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 14px;
  font-family: Arial, sans-serif;
}

input:focus, textarea:focus {
  outline: none;
  border-color: #4CAF50;
  box-shadow: 0 0 5px rgba(76, 175, 80, 0.3);
}

button {
  padding: 12px 30px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #45a049;
}

.resultado {
  margin-top: 30px;
  padding: 20px;
  background-color: #d4edda;
  border: 1px solid #c3e6cb;
  border-radius: 4px;
  color: #0c8312;
}

.resultado h2 {
  margin-top: 0;
  color: #000000;
}

.resultado p {
  margin: 10px 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}
</style>

