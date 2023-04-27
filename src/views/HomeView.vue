<template>
  <div class="home">
    <input type="text" :value="animal1Input" @input="handleAnimal1Change" />
    <p>{{animal1Input}}</p>
    <input type="text" :value="animal2Input" @input="handleAnimal2Change" />
    <p>{{animal2Input}}</p>
    <button :disabled="submitDisabled" @click="onSubmit">Submit</button>
  </div>
</template>

<script lang="ts" setup>
import { ref, computed } from "vue";
import axios, {AxiosResponse} from 'axios';

interface IAnimal {
  name: string;
  characteristics: {
    height?: string;
    length?: string;
  }
}

interface IAnimalResp {
  data: IAnimal[]
}


const baseUrl = 'https://api.api-ninjas.com/v1/animals'

const animal1Input = ref("")
const animal2Input = ref("")
const loading = ref(false)

const handleAnimal1Change = (e: InputEvent) => {
  const text = (e.target as HTMLInputElement).value;
  animal1Input.value = text
}

const handleAnimal2Change = (e: InputEvent) => {
  const text = (e.target as HTMLInputElement).value;
  animal2Input.value = text
}

const submitDisabled = computed(() => animal1Input.value.length < 1 || animal2Input.value.length < 1 || loading.value)

const onSubmit = async () => {
  try {
    loading.value = true
    // TODO REQUEST METHOD DRY
    const animal1Promise = axios.get(
      `${baseUrl}?name=${animal1Input.value}`,
      {
        headers: {
          'X-Api-Key': process.env.VUE_APP_API_KEY
        }
      }
    )
    const animal2Promise = axios.get(
      `${baseUrl}?name=${animal2Input.value}`,
      {
        headers: {
          'X-Api-Key': process.env.VUE_APP_API_KEY
        }
      }
    )
    const [animal1Resp, animal2Resp] = (await Promise.all([animal1Promise, animal2Promise])) as AxiosResponse<IAnimalResp[]>[]
    // TODO IMPROVE SELECTION PROCESS
    const animal1 = animal1Resp?.data[0];
    const animal2 = animal2Resp.data[0];
        console.log({animal1, animal2})
  } catch (err: any) {
    console.error(err.message)
  } finally {
    loading.value = false
  }
}
</script>