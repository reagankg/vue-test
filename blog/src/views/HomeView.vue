<template>
    <div class="box">
        <div class="container">
            <div class="title">Insights & Resources</div>
            <div class="subtitle">Introductory copy that goes underneath the H1 to better <br> contextualize what this does and who it's for.</div>
        </div>
    </div>
    <main>
        <div
            v-for="Post in Posts"
            :key="Post.id"
        >
            <div class="containers">
                <div>
                    <RouterLink to="/post"><img :src="Post.src" v-bind:alt="image" /></RouterLink>
                </div>
                <div class="date">
                    {{ Post.date }} | {{ Post.time }} minutes read
                </div>
                <div class="titles">
                    {{ Post.title }}
                </div>
                <div class="article">
                    {{ Post.article }}
                </div>
                <div class="align">
                    <button>How to do this</button>
                    <button>HR Stuff</button>
                </div>
            </div>
        </div>
    </main>
    <div class="load" v-if="spin">
        <button @click="loadButton">Load More</button>
    </div>
    <div class="spinner" v-else>
        <div class="loader"></div>
    </div>
</template>

<script>
import { defineComponent } from 'vue';
import Post from '../data/dataSample'
import { RouterLink, RouterView } from 'vue-router'

export default defineComponent({
    name: 'App',
    data () {
        return {
            spin: true,
            Posts: Post
        }
    },
    methods: {
        loadButton() {
            this.spin = false
        }
    }
})
</script>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Nunito+Sans&display=swap');

  body {
    font-family: 'Nunito Sans', sans-serif;
  }

.box {
    width: 100%;
    height: 277px;
    background: url("../assets/back.svg") no-repeat;
    background-size: cover;
    position: relative;
    margin-left: -8px;
    margin-right: -8px;
}

.title {
    font-family: 'Nunito Sans', sans-serif;
    font-size: 40px;
    color:white;
    line-height: 1.6;
}

.subtitle {
    font-family: 'Nunito Sans', sans-serif;
    margin-top: 20px;
    font-size: 15px;
    color:white;
    line-height: 1.6;
}

.container {
    margin: 0;
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
    margin-left: 200px;
}

main {
    margin-top: 2%;
    margin-left: 3%;
    margin-right: 5%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    flex-wrap: wrap;
}


.containers {
    /* background: red; */
    height: 420px;
    width: 300px;
    margin-left: 20px;
    margin-right: 50px;
    margin-top: 20px;
}

.containers img {
    height: 200px;
    width: 300px;
    cursor: pointer;
}

.date {
    color: aqua;
    font-size: 15px;
    margin-top: 10px;
    font-family: 'Nunito Sans', sans-serif;
}

.titles {
    color: black;
    font-size: 18px;
    margin-top: 10px;
    line-height: 100%;
    font-family: 'Nunito Sans', sans-serif;
}

.article {
    color: black;
    font-size: 15px;
    margin-top: 10px;
    font-family: 'Nunito Sans', sans-serif;
}

.align {
    display: flex;
    flex-direction: row;
    margin-top: 15px;
}

.align button{
    border: 2px solid orangered;
    border-radius: 25px;
    padding: 5px 15px 5px 15px;
    color: orangered;
    font-family: 'Nunito Sans', sans-serif;
}

button:nth-child(2){
    margin-left: 10px;
}

body {
    font-family: 'montseratt', sans-serif;
}

.load {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-top: 3%;
    margin-bottom: 3%;
}

.load button{
    cursor: pointer;
    border: 2px solid orangered;
    border-radius: 25px;
    padding: 5px 15px 5px 15px;
    color: orangered;
    font-family: 'Nunito Sans', sans-serif;
}

.spinner {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-top: 3%;
    margin-bottom: 3%;
}

.loader {
    border: 16px solid #f3f3f3;
    border-top: 16px solid orangered;
    border-radius: 50%;
    width: 120px;
    height: 120px;
    animation: spin 2s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
