<template>
  <p>
    <button v-on:click="send_store_input_customer_info()">store-input-customer-info</button>
  </p>
  <p>
    <button v-on:click="send_store_input_service_info()">store-input-service-info</button>
  </p>
  <p>
    <button v-on:click="send_assigned_customers()">assigned-customers</button>
  </p>
  <p>
    <button v-on:click="send_customer_service_history()">customer-service-history</button>
  </p>
  <p>
    <button v-on:click="send_customer_service_history_detail()">customer-service-history-detail</button>
  </p>
</template>

<script>
const axiosBase = require('axios');
const axios = axiosBase.create({
  baseURL: 'https://asia-northeast1-hackathon-202309.cloudfunctions.net', 
  headers: {
    'Content-Type': 'application/json',
  },
  responseType: 'json'  
});

export default {
  name: 'App',
  components: {
  },
  methods: {
    send_store_input_customer_info(){
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
    },
    send_store_input_service_info(){
      axios.post('/store-input-service-info', {
          "customer_id": 1001,
          "respondent_employee_line_id": "e-line-001",
          "respondent_employee_store_id": "store_id_001",
          "respondent_employee_datetime": "2023/08/31 14:30:00",
          "service_date": "2023/08/30",
          "respondent_contents_json": {
            "residential_prefecture": "東京都",
            "residential_city": "渋谷区",
            "residential_area": "奥渋谷らへん",
            "occupation": "会社員",
            "member_id": "M12345",
            "purchase_purpose": "肌寒くなってきたのでアウターが欲しい",
            "recommended_product": "商品X",
            "budget_payment_method": "予算5万円。クレジットカード",
            "size_body_type": "M",
            "preferences_style": "カジュアル",
            "hobbies_interests": "ゴルフ",
            "family_friends_info": "家族は4人兄妹です。",
            "special_events": "誕生日が来月です。",
            "cautions_complaints": "商品の交換について注意が必要です。"
          }
        })
      .then(function (response) {
        console.log(response.data);
      })
    },
    send_assigned_customers(){
      axios.post('/assigned-customers', {
        "employee_line_id": "e-line-001"
      })
      .then(function (response) {
        console.log(response.data);
      })
    },
    send_customer_service_history(){
      axios.post('/customer-service-history', {
        "employee_line_id": "e-line-001",
        "customer_id": "8"
      })
      .then(function (response) {
        console.log(response.data);
      })
    },
    send_customer_service_history_detail(){
      axios.post('/customer-service--history-detail', {
        "employee_line_id": "e-line-001",
        "customer_id": 8,
        "service_id": 123
      })
      .then(function (response) {
        console.log(response.data);
      })
    },
  }
}
</script>

<style>
  button{
    padding: 15px;
    font-size: 16px;
    border: 0px;
    border-radius: 5px;
    background: rgb(237, 209, 209);
    box-shadow: 0 3px 2px #808080;
  }
</style>
