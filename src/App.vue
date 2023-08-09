<template>
  <div class="container">


    <div class="container">
      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">İD</span>
        <input v-model="postData.id" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">Title</span>
        <input v-model="postData.title" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">Body</span>
        <input v-model="postData.body" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <button @click="onClick" type="button" class="btn btn-primary">Ekle</button>

      <h3>id = {{ postData.id }}</h3>
      <h3>title = {{ postData.title }}</h3>
      <h3>body = {{ postData.body }}</h3>


      <hr>
    </div>

    <br><br><br>
    <hr>

    <div class="container">
      <hr>
      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">İsim</span>
        <input v-model="Data.getName" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">E-mail</span>
        <input v-model="Data.getEmail" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">Adres</span>
        <input v-model="Data.getAdress" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">Web Site</span>
        <input v-model="Data.getWeb" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">Kullanıcı Adı</span>
        <input v-model="Data.getUserName" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">İD</span>
        <input v-model="Data.getID" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">Zip-Code</span>
        <input v-model="Data.getID" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>

      <div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">Input</span>
        <input v-model="Data.getID" type="text" class="form-control" aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-sm">
      </div>


      Getirmek istediğin id = <input v-model="deger" type="text">

      <br>

      <button @click="getData" type="button" class="btn btn-success">Getir</button>

    </div>

  </div>
</template>

<script>
import axios from 'axios'

export default {

  data() {
    return {
      postData: {
        id: null,
        title: null,
        body: null,
      },


      Data: {
        getName: null,
        getEmail: null,
        getAdress: null,
        getWeb: null,
        getUserName: null,
        getID: null,
      },
      deger: "",

    }
  },

  methods: {

    onClick() {

      axios.post('https://jsonplaceholder.typicode.com/posts', {

        userId: this.postData.id,
        title: this.postData.title,
        body: this.postData.body,


      })
        .then(response => console.log(response))

    },

    getData() {

      axios.get(`https://jsonplaceholder.typicode.com/users?name=${this.deger}`)
        .then(response => {
          this.Data.getName = response.data[0].name;
          this.Data.getEmail = response.data[0].email;
          this.Data.getAdress = response.data[0].address.street + " " + response.data[0].address.suite + " " + response.data[0].address.city;
          this.Data.getWeb = response.data[0].website;
          this.Data.getUserName = response.data[0].username;
          this.Data.getID = response.data[0].id;
          console.log(response.data[0].name);

        }
        )



    },


  },



  // mounted() {

  //   axios.post('https://jsonplaceholder.typicode.com/posts', {
  //     userId: "1",
  //     id: 1,
  //     title: "burası title",
  //     body: "burası body",
  //   })
  //     .then(response => console.log(response))
  // }




}


</script>

