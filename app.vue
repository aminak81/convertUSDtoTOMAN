<script setup lang="ts">
import "vue3-toastify/dist/index.css";
import '~/assets/css/first.css'
import { toast } from "vue3-toastify";
const inputValue = ref()
const dataFetch = await $fetch('http://api.navasan.tech/latest/?api_key=freegvwLhKjDEi4iQQV2qWGYk62Vlbnb')
function calcDoller() {
  const tempCalc =  parseInt(inputValue.value) * parseInt(dataFetch.usd_sell.value)
  if(!inputValue.value || inputValue.value.trim() === ""){
    toast('لطفا مقدار وارد کنید', {
      "theme": "colored",
      "type": "warning",
      "position": "top-center",
      "autoClose": 840,
      "hideProgressBar": false,
      "transition": "slide",
      "dangerouslyHTMLString": true
    });
  }else {
    toast('قیمت این لحظه : ' + numberSeparator(tempCalc) + ' تومان ', {
      "theme": "light",
      "type": "default",
      "position": "top-center",
      "autoClose": 840,
      "hideProgressBar": false,
      "transition": "slide",
      "dangerouslyHTMLString": true
    });
  }}
function numberSeparator (number: any) {
  number = parseInt(number)
  return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
}


</script>
<template>
  <v-container
      col="12"
      style="height: 100vh;
      background-color:#BA0021;"
      fluid
      class="d-flex align-center"
  >
    <v-row
        col="12"
    >
      <v-col
          cols="12"
          class="text-center"

      >
        <v-card
            class="mx-auto text-center align-content-center rounded-xl elevation-12"
            subtitle="first project"
            max-width="375"
            min-height="320"
        >
          <template v-slot:title>
            <span style="font-weight: bold;font-size : 32px;">Convert USD to TOMAN</span>
          </template>
          <template v-slot:text>
            <v-text-field
                v-model="inputValue"
                class="mx-auto"
                label="Input"
                placeholder="Enter your Toman"
                clearable
            />
            <v-btn
                color="#BA0021"
                font-weight="900"
                size="large"
                type="submit"
                variant="elevated"
                text="Convert"
                block
                @click="calcDoller"
            />
          </template>

        </v-card>

        <p
            style="color:whitesmoke;"
            class="text-h6 mt-2 font-weight-black" >Copyright 🤍
        </p>
      </v-col>
    </v-row>
  </v-container>
</template>

<style>
* {
  font-family: 'Peyda', sans-serif;
}
</style>