<template>
<div>
  <div>
  <h1>ログインユーザ</h1>
  <form @submit.prevent="loginUser">
    <v-row>
      <v-col cols="12" sm="6" md="3">
        <v-text-field
          v-model="user.email"
          label="Eメール"
        >
        </v-text-field>
      </v-col> 
    </v-row>
    <div class="form-group">
    <v-row>
      <v-col cols="12" sm="6" md="3">
        <v-text-field
          v-model="user.password"
          label="パスワード"
        >
        </v-text-field>
      </v-col> 
    </v-row>
    </div>
    <v-btn color="primary" type="/submit">
      ログイン
    </v-btn>
  </form>
  </div>
</div>
</template>

<script>
  export default {
    data(){
      return {
        user:{
          email:'',
          password:''
        }
      }
    },
    methods:{
      loginUser(){
        this.$auth.loginWith('local',{
          data:this.user
        })
      },
    }
  }
</script>
