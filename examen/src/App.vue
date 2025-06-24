<script setup>
import {reactive} from 'vue'

const userInput = reactive({
 name: "",
 phoneNumber: "",
 date: "",
 time: "",
 dlitelnost:"",
 yesYouCan : false
})
const errors = reactive({
 name: "",
 phoneNumber: "",
 date: "",
 time: "",
 dlitelnost:""
})


// 2025-06-26

function createBron() {
  const regixName = /^[А-ЯЁ][а-яё]+$/
  const regixPhoneNumber = /^[0-9]+$/
  const regixDate = /^2025-06-25|2025-06-26|2025-06-27|2025-06-28|2025-06-29|2025-06-30/

  let flag = true


  if(regixName.test(userInput.name)){
    errors.name = ""
  }else{
    errors.name = "ИМЯ ЖИВО по примеру 'Иван'" 
    flag = false
  }
  
  if(userInput.phoneNumber.length == 11 && regixPhoneNumber.test(userInput.phoneNumber)){
    errors.phoneNumber = ""
  }else{
    errors.phoneNumber = "Мобилу гони"
    flag = false 
  }
  
  if(userInput.date != ""){
    if(regixDate.test(userInput.date)){
      errors.date = ""
    }
  }else{
    errors.date = "Ты с датой то разберись" 
    flag = false
  }

  if(userInput.time != ""){
    errors.time = ""
  }else{
    errors.time = "Тик так, время на бочку" 
    flag = false
  }

  if(userInput.dlitelnost != ""){
    errors.dlitelnost =""
  }else{
    errors.dlitelnost = "Сколько сидеть планируешь" 
    flag = false
  }

  if(flag && userInput.yesYouCan){
    userInput.name = ""
    userInput.phoneNumber = ""
    userInput.date = ""
    userInput.time = ""
    userInput.dlitelnost =""
    userInput.yesYouCan  = false
    
    alert("Имя: " + userInput.name + "\n" + "Телефон: " + userInput.phoneNumber + "\n" + "Дата: " + userInput.date + "\n" +"Время: " + userInput.time+":00" + "\n" +"Длительность: " + userInput.name+"ч")
  }
}

</script>

<template>
  <div class="main">

  <h1>БРОНЬ</h1>
  <div class="input">
    <p>Имя</p>
    <input type="text" placeholder="Иван" v-model="userInput.name">
    <p class="error">{{ errors.name }}</p>
    <p>Телефон</p>
    <input type="text" placeholder="80000000000" v-model="userInput.phoneNumber">
    <p class="error">{{ errors.phoneNumber }}</p>
    
    
    <p>Дата(25-30 Июня)</p>
    <input type="date" placeholder="25.06.2025" v-model="userInput.date">
    <p class="error">{{ errors.date }}</p>


    <p>Время</p>
    <select name="" id="" v-model="userInput.time">
      <option value="12">12:00</option>
      <option value="13">13:00</option>
      <option value="14">14:00</option>
      <option value="15">15:00</option>
      <option value="16">16:00</option>
      <option value="17">17:00</option>
      <option value="18">18:00</option>
      <option value="19">19:00</option>
      <option value="20">20:00</option>
    </select>
    <p class="error">{{ errors.time }}</p>

    <p>Длительность брони</p>
    <select name="" id="" v-model="userInput.dlitelnost">
      <option value="1">1 часов</option>
      <option value="3">3 часов</option>
      <option value="5">5 часов</option>
    </select>
    <p class="error">{{ errors.dlitelnost }}</p>

    <p><input type="checkbox" value="true" v-model="userInput.yesYouCan">Ты Уверен</p>
    <button @click="createBron">забронировать</button>
  </div>

  <footer>
    <h1>@2025 VADIM BOROVIKOV</h1>
  </footer>
  </div>

</template>

<style scoped>
.main{
  display: flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
  padding: 1vw;
}
.input{
  display: flex;
  flex-direction: column;
  gap: 1vw;
  padding: 3vw;
}
.error{
  color: red;
}
footer{
  color: white;
  align-items: center;
  text-align: center;
  padding: 3vw;
  padding-bottom: -30vw;  
  background-color: black;
  width: 70vw;
  height: 10vw;
  border-radius: 1vw;
}
</style>
