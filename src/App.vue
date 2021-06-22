<template>
  <div class="container">
    <div>
      <h3>Информация</h3>
      <div class="input-group" :class="{error : isError(v$.form.surname)}">
        <label>Фамилия *</label>						
        <input type="text" v-model="form.surname" @blur="v$.form.surname.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.form.name)}">
        <label>Имя *</label>						
        <input type="text" v-model="form.name" @blur="v$.form.name.$touch()">
        <div class="err-message">Это поле обязательное для заполнения. </div>
      </div>

      <div class="input-group" :class="{error : isError(v$.form.fatherName)}">
        <label>Отчество</label>						
        <input type="text" v-model="form.fatherName" @blur="v$.form.fatherName.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.form.bdate)}">
        <label>Дата рождения *</label>						
        <input type="date" v-model="form.bdate" @blur="v$.form.bdate.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.form.phone)}">
        <label>Номер телефона *</label>						
        <input type="text" v-model="form.phone" @blur="v$.form.phone.$touch()">
        <div class="err-message">Введите номер из 11 цифр, начиная с 7.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.form.sex)}">
        <label>Пол</label>						
        <input type="text" v-model="form.sex" @blur="v$.form.sex.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.form.clients)}">
        <label>Группа клиентов *</label>						
        <select name="" id="" multiple v-model="form.clients" @blur="v$.form.clients.$touch()">
          <option v-for="(client, index) in form.allClients" :key="index" :value="client.value">{{client.label}}</option>
        </select>
        <div class="err-message">Укажите как минимум одну группу.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.form.doctor)}">
        <label>Лечащий врач</label>						
        <select name="" id="" v-model="form.doctor" @blur="v$.form.doctor.$touch()">
          <option v-for="(doctor, index) in form.allDoctors" :key="index" :value="doctor.value">{{doctor.label}}</option>
        </select>
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group">
        <label><input type="checkbox" v-model="form.sms" @blur="v$.form.sms.$touch()">Не отправлять СМС</label>						
      </div>
    </div>

    <div>
      <h3>Адрес</h3>
      <div class="input-group" :class="{error : isError(v$.address.index)}">
        <label>Индекс</label>						
        <input type="text" v-model="address.index" @blur="v$.address.index.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.address.country)}">
        <label>Страна</label>						
        <input type="text" v-model="address.country" @blur="v$.address.country.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.address.region)}">
        <label>Область</label>						
        <input type="text" v-model="address.region" @blur="v$.address.region.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.address.city)}">
        <label>Город *</label>						
        <input type="text" v-model="address.city" @blur="v$.address.city.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.address.street)}">
        <label>Улица</label>						
        <input type="text" v-model="address.street" @blur="v$.address.street.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.address.numBuild)}">
        <label>Дом</label>						
        <input type="text" v-model="address.numBuild" @blur="v$.address.numBuild.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>
    </div>

    <div>
      <h3>Паспорт</h3>
      <div class="input-group" :class="{error : isError(v$.document.type)}">
        <label>Тип документа *</label>						
        <select name="" id="" v-model="document.type" @blur="v$.document.type.$touch()">
          <option v-for="(type, index) in document.allTypes" :key="index" :value="type.value">{{type.label}}</option>
        </select>
        <div class="err-message">Это поле обязательное для заполнения. </div>
      </div>

      <div class="input-group" :class="{error : isError(v$.document.series)}">
        <label>Серия</label>						
        <input type="text" v-model="document.series" @blur="v$.document.series.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.document.number)}">
        <label>Номер</label>						
        <input type="text" v-model="document.number" @blur="v$.document.number.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.document.givenBy)}">
        <label>Кем выдан</label>						
        <input type="text" v-model="document.givenBy" @blur="v$.document.givenBy.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>

      <div class="input-group" :class="{error : isError(v$.document.date)}">
        <label>Дата выдачи *</label>						
        <input type="date" v-model="document.date" @blur="v$.document.date.$touch()">
        <div class="err-message">Это поле обязательное для заполнения.</div>
      </div>
    </div>
  </div>

  <div class="alert" v-if="alert">
    <div class="alert__box">
      Новый клиент успешно создан.
      <div class="but" @click="alert=false">
        Закрыть
      </div>
    </div>
  </div>
  
  <div class="but" @click=send()>
    Сохранить
  </div>
</template>

<script>
import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'
import { ref } from 'vue'

export default {
  name: 'App',
  components: {
  },
  setup () {
    const alert = ref(false)
    return { 
      alert,
      v$: useVuelidate()
    }
  },
  methods: {
    send() {
      this.v$.$touch()

      if (!this.v$.$invalid) {
        this.alert = true
      }
    },
    isError(obj) {
      return obj.$invalid && obj.$dirty
    }
  },
  data () {
    return {
      form: {
        surname: '',
        name: '',
        fatherName: '',
        bdate: '',
        phone: '',
        sex: '',
        clients: ['vip'],
        allClients: [{label: 'VIP', value: 'vip'}, {label: 'Проблемные', value: 'problem'}, {label: 'ОМС', value: 'omc'}],
        doctor: '',
        allDoctors: [{label: 'Иванов', value: 'Ivanov'}, {label: 'Захаров', value: 'Zakharov'}, {label: 'Чернышева', value: 'Chernisheva'}],
        sms: false
      },
      address: {
        index: '',
        country: '',
        region: '',
        city: '',
        street: '',
        numBuild: ''
      },
      document: {
        type: 'passport',
        allTypes: [{label: 'Паспорт', value: 'passport'}, {label: 'Свидетельство о рождении', value: 'birth-cert'}, {label: 'Вод. удостоверение', value: 'driver-lis'}],
        series: '',
        number: '',
        givenBy: '',
        date: ''
      }
    }
  },
  validations () {
    return {
      form: {
        surname: { required },
        name: { required },
        fatherName: {},
        bdate: { required },
        phone: { required, phoneValid: (value) => /^7\d{10}$/.test(value) },
        sex: {},
        clients: { required },
        doctor: {},
        sms: {}
      },
      address: {
        index: {},
        country: {},
        region: {},
        city: { required },
        street: {},
        numBuild: {}
      },
      document: {
        type: {},
        series: {},
        number: {},
        givenBy: {},
        date: { required }
      }
    }
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

@media screen and (max-width: 700px) {
  .container {
    grid-template-columns: 1fr;
  }
}

.input-group, h3 {
  color: #333;
  font-family: Helvetica, Arial, sans-serif;
  line-height: 20px;
}

h3 {
  text-align: center;
}

.input-group {
  font-size: 13px;
  margin: 0 20px;
}

label {
  font-weight: 700;
  display: block;
  margin-bottom: 2px;
  user-select: none;
}

input, select {
  min-height: 30px;
  border: 1px solid silver;
  border-radius: 4px;
  background: white;
  padding: 5px 10px;
  width: 100%;
}

input[type="checkbox"] {
  min-height: unset;
  width: unset;
  float: left;
}

select[multiple] {
  padding: 0;
}

select, option {
  padding: 0 10px;
}

.err-message {
  opacity: 0;
  color: #cc0033;
  font-size: 12px;
  line-height: 15px;
  margin: 5px 0 0;
  user-select: none;
}

.error .err-message {
  opacity: 1;
}

.error input, .error select {
  border-color: red;
  background: #fdd;
  outline: none;
}

.error label {
  color: #cc0033;
}

.but {
  background: #b6c6ff;
  text-align: center;
  border-radius: 5px;
  padding: 5px;
  cursor: pointer;
  margin: 10px 15px;
  transition: .2s;

  &:hover {
    background: #6183ff;
  }
}

.alert {
  z-index: 100;
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba($color: #000000, $alpha: 0.5);

  &__box {
    padding: 10px 20px;
    background: white;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
}
</style>
