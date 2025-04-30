<template>
    <div>
      <h1>Курсы валют ЦБ РФ</h1>
      <div v-if="loading">Загрузка данных...</div>
      <div v-else-if="error">{{ error }}</div>
      <ul v-else>
        <li v-for="currency in currencies" :key="currency.CharCode">
          {{ currency.CharCode }}: {{ currency.Value }} ₽ ({{ currency.Name }})
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue'
  import { parseString } from 'xml2js'
  
  const currencies = ref([])
  const loading = ref(true)
  const error = ref(null)
  
  onMounted(async () => {
    try {
      const xmlData = await $fetch('http://www.cbr.ru/scripts/XML_daily.asp?date_req=02/03/2002')
      
      parseString(xmlData, (err, result) => {
        if (err) throw new Error('Ошибка парсинга XML')
        
        // Преобразуем структуру данных
        currencies.value = result.ValCurs.Valute.map(item => ({
          CharCode: item.CharCode[0],
          Name: item.Name[0],
          Value: item.Value[0],
          Nominal: item.Nominal[0]
        }))
        
        console.log('Данные получены:', currencies.value)
      })
    } catch (err) {
      error.value = 'Не удалось загрузить курсы валют: ' + err.message
      console.error(err)
    } finally {
      loading.value = false
    }
  })
  </script>
  
  <style>
  /* Ваши стили */
  </style>