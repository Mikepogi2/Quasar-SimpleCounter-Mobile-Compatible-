<template>
  <q-page class="flex flex-center" style="max-width: 600px; margin: 0 auto;" v-touch-swipe.mouse="handleSwipe">
    <div class="row">
      <q-input v-model="data.name" placeholder="Counter" filled input-class="text-center text-h6" color="white"/>
    </div>
    <div class="row full-width items-center">
      <div class="col text-center">
        <q-btn outline round color="dark" icon="remove" size="22px" @click="minusNum" v-touch-repeat:300:300:100.mouse="minusNum"/>
      </div>
      <div class="col text-center text-h2">
        {{ data.number }}
      </div>
      <div class="col text-center">
        <q-btn outline round color="dark" icon="add" size="22px" @click="addNum" v-touch-repeat:300:300:100.mouse="addNum"/>
      </div>
    </div>
    <div class="row text-center">
      <q-btn outline round color="dark" icon="restart_alt" size="22px" @click="number = 0"/>
    </div>
  </q-page>
</template>

<script setup>
import { reactive, ref, watch } from 'vue';
import { useQuasar } from 'quasar';
const $q = useQuasar()

const data = reactive({
  number: 0,
  name: ''
})

const minusNum = () => {
  if (data.number > 0) data.number--
}

const addNum = () => {
  data.number++
}

const handleSwipe = e => {
  console.log(e.direction)
  if(e.direction == 'up') addNum()
  else if(e.direction == 'down') minusNum()
}

const SaveData = $q.localStorage.getItem('data')
if (SaveData) Object.assign(data, SaveData)

watch(data, value => {
  console.log(value)
  $q.localStorage.set('data', value)
})

</script>
