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
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@500&display=swap');
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

:root{
    --light-cyan: hsl(193, 38%, 86%);
    --neon-green: hsl(150, 100%, 66%);
    --grayish-blue: hsl(217, 19%, 38%);
    --dark-grayish-blue: hsl(217, 19%, 24%);
    --dark-blue: hsl(218, 23%, 16%);
}

body{
    font-family: 'Manrope', sans-serif;
    background: var(--dark-blue);
}

.container{
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.card{
    width: 550px;
    max-width: 90%;
    min-height: 300px;
    text-align: center;
    background: var(--dark-grayish-blue);
    border-radius: 25px;
}

.advice-id{
    color: var(--neon-green);
    letter-spacing: 5px;
    margin: 25px auto;
    transform: translateY(15px);
}

.advice{
    width: 90%;
    min-height: 120px;
    font-size: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: var(--light-cyan);
    margin: 15px auto;
    transform: translateY(10px);
}

.divider{
    width: 90%;
    height: 30px;
    transform: translateY(35px);
    background: url('../assets/images/pattern-divider-desktop.svg') no-repeat center;
    margin: 15px auto;
}

.generator{
    width: 60px;
    height: 60px;
    border-radius: 50%;
    border: none;
    transform: translateY(30px);
    background: var(--neon-green);
    transition: 0.3s ease-out;
    cursor: pointer;
}

.generator:hover{
    box-shadow: 0px 0px 20px 5px var(--neon-green);
}

.author{
    position: fixed;
    max-width: 90%;
    margin: auto;
    bottom: 15px;
    color: var(--light-cyan);
}

a{
    color: var(--neon-green);
}

@media (max-width: 420px){
    .advice{
        font-size: 25px;
        transform: translateY(30px);
    }
    .divider{
        background: url('../assets/images/pattern-divider-mobile.svg') no-repeat center;
    }
}
</style>