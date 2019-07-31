<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>Github User</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <UserSearch v-on:get-user="getUserInfo"/>
      <UserInfo v-bind:info="info"/>
      <ClearInfo v-bind:info="info" v-on:clear-info="clearInfo"/>
    </ion-content>

  </div>
</template>

<script>
  import UserSearch from '../components/UserSearch';
  import UserInfo from '../components/UserInfo';
  import ClearInfo from '../components/ClearInfo';
  export default {
    name: 'home',
    components: {
      UserSearch, UserInfo, ClearInfo
    },
    data: function(){
      return{
        info: null
      }
    },
    methods:{
      async getUserInfo(user){
        const res = await fetch(`https://api.github.com/users/${user}`);
        if (res.status == 404){
          this.showAlert();
          this.info = null;
          //this.$emit('clear-info');
        }
        this.info = await res.json();
      },
      clearInfo(){
        this.info = null;
      },
      showAlert(){
        return this.$ionic.alertController
          .create({
            header: "that user doesn't exist",
            message: 'Please enter a valid username',
            buttons: ['OK']
          })
          .then(a => a.present());
      }
    }
  }
</script>