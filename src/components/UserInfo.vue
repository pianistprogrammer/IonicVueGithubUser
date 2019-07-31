<template>
    <ion-card v-if="info">
        <ion-card-header>
            <ion-card-subtitle class="ion-text-center">
                {{info.login}}
            </ion-card-subtitle>
            
            <ion-card-title class="ion-text-center">
                {{info.name}}
            </ion-card-title>
            <img class="img-search" :src="info.avatar_url"/>
        </ion-card-header>
        <ion-card-content>
            <ion-list>
                <ion-item>
                    <ion-label>
                        <strong>Pubic repos: </strong>
                        {{info.public_repos}}
                    </ion-label>
                </ion-item>
                <ion-item>
                    <ion-label>
                        <strong>Followers: </strong>
                        {{info.followers}}
                    </ion-label>
                </ion-item>
            </ion-list>
        </ion-card-content>
    </ion-card>
</template>

<script>
export default {
    name: 'UserInfo',
    props:['info']
}
</script>

 <style scoped>
 .img-search{
    border-radius: 50%;
    border: 8px solid #ccc;
    margin-top: 30px;
    margin-bottom: 20px;
 }
 </style>
 