<script setup lang="ts">
import pokemon from 'pokemontcgsdk'

const config = useRuntimeConfig()

const PKMN_API = config.PKMN_API_KEY

pokemon.configure({apiKey: PKMN_API})

const test = ref("")

const getTestData = async () => {
  try {
    const data = await pokemon.card.where({ q: 'name:blastoise', pageSize: 10, page: 3 })
    test.value = data.data[0].cardmarket.prices
  } catch (error) {
    console.log(error)
  }
}

onMounted(() => {
  getTestData()
})
</script>

<template>
  <div>
    <div>TEST aREa</div>
    <pre>{{ test }}</pre>
  </div>
</template>

<style scoped lang="scss">

</style>