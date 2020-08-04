<template>
<div>
  <div>
  <h1>ユーザ登録</h1>
  <form @submit.prevent="registerShop">
    <v-row>
      <v-col cols="12" sm="6" md="3">
        <v-text-field
          v-model="shop.name"
          label="名前"
        >
        </v-text-field>
      </v-col> 
    </v-row>
    <v-row>
      <v-col cols="12" sm="6" md="3">
        <v-text-field
          v-model="shop.place"
          label="位置情報"
        >
        </v-text-field>
      </v-col> 
    </v-row>
    <div class="form-group">
    <v-row>
      <v-col cols="12" sm="6" md="3">
        <v-text-field
          :value="$auth.user.id"
          label="ShopManager ID"
          key="shop.id"
          readonly
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
        shop:{
          name:'',
          place:'',
        }
      }
    },
    methods:{
      registerShop(){
        this.$axios.post('/api/shop/register/',this.shop)
                    .then((response) => {
                        this.$auth.loginWith('local',{
                            data: this.shop
                    })
        })
      },
    }
  }
</script>