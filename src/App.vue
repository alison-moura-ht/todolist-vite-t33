<template>
  <h1 class="mt-32 text-center text-4xl font-bold text-gray-600">{{ titulo }}</h1>

  <div class="container p-10 bg-blue-400 w-4/5 md:w-1/2 lg:w-1/4 mx-auto mt-10 rounded">
    <app-input>
      <input
        class="outline-none w-full"
        v-model="tarefa.descricao"
        type="text"
        placeholder="Descrição da tarefa"
      />
    </app-input>
    <app-btn class="mt-5 mx-auto" @click="adicionarTarefa">Adicionar</app-btn>
  </div>

  <div class="w-4/5 lg:w-1/2 mx-auto">
    <div class="bg-white shadow-md rounded my-6 overflow-hidden overflow-x-scroll">
      <table class="min-w-max w-full sm:table-auto lg:table-fixed">
        <thead>
          <tr class="bg-blue-400 text-white uppercase text-sm leading-normal">
            <th class="py-3 px-5 text-center">Concluída</th>
            <th class="w-3/5 py-3 px-5 text-center">Descrição</th>
            <th class="py-3 px-5 text-center">Remover</th>
          </tr>
        </thead>
        <tbody class="text-gray-600 text-sm font-light">
          <tr
            v-for="(iterador, indice) in tarefas"
            :key="iterador"
            :class="{ riscado: iterador.concluida }"
            class="border-b border-gray-200 hover:bg-gray-100"
          >
            <td class="py-3 px-6 text-left whitespace-nowrap">
              <div class="flex items-center">
                <input type="checkbox" v-model="iterador.concluida" />
              </div>
            </td>
            <td class="py-3 px-6 text-left overflow-x-scroll">{{ iterador.descricao }}</td>
            <td class="py-3 px-6">
              <svg
                @click="remover(indice)"
                class="mx-auto"
                style="width: 20px"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
                />
              </svg>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import AppBtn from "./components/AppBtn.vue";
import AppInput from "./components/AppInput.vue"
import { reactive, ref, onMounted } from "vue"

// Composition API
const titulo = ref("Todolist")
const tarefas = reactive([])
const tarefa = reactive({
  descricao: "",
  concluida: false
})

function adicionarTarefa() {
  tarefas.push(Object.assign({}, tarefa));
}

function remover(indice) {
  tarefas.splice(indice, 1)
}

</script>

<style>
.riscado {
  text-decoration: line-through;
}
</style>