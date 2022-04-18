<template>
  <div class="container">
      <div class="card">
          <h5 class="advice-id">
              ADVICE #{{adviceID}}
          </h5>
          <h1 class="advice">
              <q>
                  {{advice}}
              </q>
          </h1>
          <div class="divider"></div>
          <button @click="getAdvice" class="generator">
              <img src="@/assets/images/icon-dice.svg" alt="Dice">
          </button>
      </div>
      <div class="author">
          <h5>Challenge by <a href="https://frontendmentor.io" target="_blank">Frontend Mentor</a> Coded by <a href="https://github.com/ArturHarutyunyan1" target="_blank">Artur Harutyunyan</a></h5>
      </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            adviceID: "117",
            advice: "It is easy to sit up and take notice, what's difficult is getting up and taking action"
        }
    },
    methods:{
       async getAdvice(){
            try {
                const res  = await fetch(`https://api.adviceslip.com/advice`)
                const data = await res.json()
                this.adviceID = data.slip.id
                this.advice   = data.slip.advice 
            } catch (error) {
                console.log(error);
            }
        }
    }
}
</script>

<style>
@import '../assets/css/style.css';
</style>