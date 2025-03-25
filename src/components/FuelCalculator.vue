<script setup lang="ts">
import { ref } from 'vue'

const fuelPerLap = ref(0)
const lapTimeInSeconds = ref(0)
const raceDurationInMinutes = ref(0)
const fuelNeeded = ref(0)
const numberOfLaps = ref(0)

const calculateNumberOfLaps = () => {
  numberOfLaps.value = Math.ceil((raceDurationInMinutes.value * 60) / lapTimeInSeconds.value)
}

const calculateFuelNeeded = () => {
  fuelNeeded.value =
    Math.ceil((raceDurationInMinutes.value * 60) / lapTimeInSeconds.value) * fuelPerLap.value
}
</script>

<template>
  <div class="fuel-calculator">
    <div class="calculation-inputs">
      <div class="fuel-per-lap">
        <label for="fuelPerLap">Fuel per lap: </label>
        <input type="number" v-model="fuelPerLap" />
      </div>
      <div class="lap-time-in-seconds">
        <label for="lapTimeInSeconds">Lap time in seconds: </label>
        <input type="number" v-model="lapTimeInSeconds" />
      </div>
      <div class="race-duration">
        <label for="raceDurationInMinutes">Race duration: </label>
        <input type="number" v-model="raceDurationInMinutes" />
      </div>
      <div class="number-of-laps">
        <button @click="calculateNumberOfLaps">Calculate number of laps</button>
      </div>
      <div class="fuel-needed">
        <button @click="calculateFuelNeeded">Calculate fuel needed</button>
      </div>
    </div>
    <div class="calculation-results">
      <p>Number of laps: {{ numberOfLaps }}</p>
      <p>Fuel needed: {{ fuelNeeded }}</p>
    </div>
  </div>
</template>
