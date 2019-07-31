<template>
    <ion-grid>
        <ion-button color='light' expand='block' v-if="info" @click="$emit('clear-info')">
        Clear
    </ion-button>
    </ion-grid>
    
</template>

<script>
export default {
    name:'ClearInfo',
    props:['info']
}
</script>
 
