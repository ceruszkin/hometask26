<script>
    import axios from "axios";

    export default {
        beforeMount: function (el) {
            axios.get("https://fakestoreapi.com/products").then((response) => {
                console.log(response.data)
                this.list = response.data
            }) 
        },
        data() {
            return {
                title: "Список новостей",
                list: []
            };
        },
        setup() {
            return {

            }
        }
    }
</script>

<template>
    <h1>{{ title }}</h1>
    <section>
        <div class="good-list">
            
                <div class="good-list__item" v-bind:key="item.id" v-for="item in list">
                    <router-link v-bind:to="'/news/' + item.id">
                        <img class="good-list__img" v-bind:src="item.image" v-bind:alt="item.title">
                        <span class="good-list__title">{{ item.title }}</span>
                    </router-link>
                </div>
        </div>
    </section>
</template>

<style scoped>
    .good-list{
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
    .good-list__item{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        margin-right: 100px;
        margin-bottom: 15px;
        width: 250px; 
        height: 370px;
        border-radius: 10px;
        background-color: #DDC8C4;
        color: #896A67;
    }
    .good-list__img{
        display: flex;
        align-items: center;
        margin-top: 15px;
        max-height: 200px;
        max-width: 200px;
        border-radius: 10px;
    }

    .good-list__title{
        display: flex;
        flex-wrap: wrap;
        text-align: center;
        color: #896A67
    }
</style>