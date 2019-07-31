<template>
    <ion-grid>
        <form @submit="submitForm">
            <ion-col>
                <ion-item>
                    <ion-label>Username:  </ion-label>
                    <ion-input :value="user" @input="user = $event.target.value" placeholder="Enter the username" name="user"></ion-input>
                </ion-item>
            </ion-col>
            <ion-col>
                <ion-button type="submit" color="primary" expand="block">Find</ion-button>
            </ion-col>
        </form>
    </ion-grid>
</template>

<script>
export default {
    name:'UserSearch',
    data: function(){
        return {
            user: ''
        }
    },
    methods:{
        submitForm(e){
            e.preventDefault();
            this.$emit('get-user', this.user);
            this.user = '';
        }
    }
}
 
</script>

