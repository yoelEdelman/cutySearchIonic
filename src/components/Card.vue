<template>
    <ion-card>
        <ion-card-header>
            <img alt="Vue logo" src="../assets/finger.png">
            <ion-card-subtitle v-if="subtitle">{{ subtitle}}</ion-card-subtitle>
            <ion-card-title>{{title}}</ion-card-title>
        </ion-card-header>
        <ion-card-content v-if="body">
            {{ body }}
        </ion-card-content>
        <div style="padding-bottom: 10px" v-if="postCode">Départements : <button @click="open = !open"> ▼ </button></div>
        <div v-if="postCode" class="collapse" :class="{'open': open === true}">
            <article style="margin: 4px">
                <span style="margin: 5px" v-for="(code, index) in  postCode">
                    {{ code }}
                </span>
            </article>
        </div>

    </ion-card>
</template>

<style scoped>

    .collapse{
        height: 0px;
        overflow: hidden;
        transition: 0.5s linear ;
    }

    .open{
        height: auto;
    }

    button{
        outline: none;
        background: none;
    }

</style>
<script>
    export default {
        name: "card",
        props: {
            title: {
                type: String,
            },
            subtitle: {
                type: String,
            },
            body :{
                type : String
            },
            postCode : {
                type : Array
            }
        },
        data (){
            return{
                open : false
            }
        }
    }
</script>