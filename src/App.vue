<template>
  <button v-on:click="sendPost()">SEND!!!</button>
</template>

<script>
const axiosBase = require('axios');
const axios = axiosBase.create({
  baseURL: 'https://asia-northeast1-hackathon-202309.cloudfunctions.net', 
  headers: {
    'Content-Type': 'application/json',
    'X-Requested-With': 'XMLHttpRequest'
  },
  responseType: 'json'  
});

export default {
  name: 'App',
  components: {
  },
  methods: {
    sendPost(){
      axios.post('/store-input-customer-info', {
        "family_name": "鈴木",
        "first_name": "太郎",
        "customer_name": "丸メガネをかけた男性",
        "sex": "男性",
        "age_bin": "30歳-35歳",
        "customer_line_id": "abc123",
        "customer_id_external": "ext001"
      })
      .then(function (response) {
        console.log(response.data);
      })
    }
  }
}
</script>

<style>
</style>
