<template>
  <v-container class="mt-15">
    <v-card elevation="20" color="black">
      <v-card-title>
        <v-container>
          <v-row>
            <v-col cols="12">
              <h1 class="text-center">Calculadora</h1>
            </v-col>
          </v-row>
        </v-container>
      </v-card-title>
    </v-card>
    <v-container>
      <v-card elevation="10" class="text-center py-2 px-4">
        <v-container>
          <v-row>
            <v-col cols="12">
              <!-- Pantalla de la calculadora -->
              <v-text-field v-model="display" readonly class="text-right" variant="outlined"></v-text-field>
            </v-col>
          </v-row>
          <v-row class="d-flex justify-center">
            <v-col cols="6" md="3" v-for="button in buttons" :key="button">
              <v-btn @click="addToDisplay(button)" rounded color="black" large>{{ button }}</v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-card>
    </v-container>
  </v-container>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const display = ref('');

const buttons = [
  '7', '8', '9', '/',
  '4', '5', '6', '*',
  '1', '2', '3', '-',
  'C', '0', '=', '+'
];

function addToDisplay(value: string) {
  if (value === '=') {
    // Calcular resultado
    display.value = eval(display.value);
  } else if (value === 'C') {
    // Limpiar pantalla
    display.value = '';
  } else {
    // Agregar valor a la pantalla
    display.value += value;
  }
}
</script>
