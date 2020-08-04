<template>
<div>
  <div>
  <h1>ユーザ登録</h1>
  <form @submit.prevent="registerUser">
    <v-row>
      <v-col cols="12" sm="6" md="3">
        <v-text-field
          v-model="user.name"
          label="名前"
        >
        </v-text-field>
      </v-col> 
    </v-row>
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
          :type="show2 ? 'text' : 'password'"
          label="パスワード"
        >
        </v-text-field>
      </v-col> 
    </v-row>
    </div>
    <v-btn color="primary" type="submit">
      登録
    </v-btn>
  </form>
  </div>
</div>
</template>

<script>
  export default {
  auth: false,
    data(){
      return {
        user:{
          name:'',
          email:'',
          password:''
        }
      }
    },
    methods:{
      registerUser(){
        this.$axios.post('/api/auth/register',this.user)
                    .then((response) => {
                        this.$auth.loginWith('local',{
                            data: this.user
                    })
        })
      },
    }
  }
</script>