<script setup>
import { ref, reactive } from "vue";
import Alerta from "./Alerta.vue";

const alerta = reactive({
  tipo: "",
  mensaje: "",
});

const paciente = reactive({
  nombre: "",
  propietario: "",
  email: "",
  sintomas: "",
  alta: "",
});

const validar = () => {
  if (Object.values(paciente).includes("")) {
    alerta.mensaje = "Todos los campos Son Obligatorios";
    alerta.tipo = "error";
    return;
  }
};
</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Añade Pacientes y
      <span class="text-indigo-600 font-bold">Administralos</span>
    </p>
    <Alerta v-if="alerta.mensaje" :alerta="alerta" />
    <form
      class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
      @submit.prevent="validar"
    >
      <div class="mb-5">
        <label for="mascota" class="block text-gray-700 uppercase font-bold">
          Nombre Mascota:
        </label>
        <input
          type="text"
          id="mascota"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          placeholder="Nombre Mascota"
          v-model="paciente.nombre"
        />
      </div>
      <div class="mb-5">
        <label
          for="propietario"
          class="block text-gray-700 uppercase font-bold"
        >
          Nombre Propietario:
        </label>
        <input
          type="text"
          id="propietario"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          placeholder="Nombre Propietario"
          v-model="paciente.propietario"
        />
      </div>
      <div class="mb-5">
        <label for="email" class="block text-gray-700 uppercase font-bold">
          Correo:
        </label>
        <input
          type="email"
          id="email"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          placeholder="Correo"
          v-model="paciente.email"
        />
      </div>
      <div class="mb-5">
        <label for="alta" class="block text-gray-700 uppercase font-bold">
          Alta:
        </label>
        <input
          type="date"
          id="alta"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          placeholder="Alta"
          v-model="paciente.alta"
        />
      </div>
      <div class="mb-5">
        <label for="sintomas" class="block text-gray-700 uppercase font-bold">
          Sintomas:
        </label>
        <textarea
          id="sintomas"
          placeholder="Describe los sintomas"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-32"
          v-model="paciente.sintomas"
        ></textarea>
      </div>

      <input
        type="submit"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-800 cursor-pointer transition-colors"
        value="Registrar Paciente"
      />
    </form>
  </div>
</template>
