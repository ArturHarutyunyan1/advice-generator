<template>
  <div class="container">
      <div class="card" v-for="res in result" :key="res">
          <p class="adviceID">ADVICE #{{res.id}}</p>
          <q class="advice">
              {{res.advice}}
          </q>
          <div class="divider">
              <img src="@/assets/pattern-divider-desktop.svg" alt="divider" class="desktop">
              <img src="@/assets/pattern-divider-mobile.svg" alt="divider" class="mobile">
          </div>
          <button @click="generateAdvice" class="btn">
              <img src="@/assets/icon-dice.svg" alt="dice">
          </button>
      </div>
      <div class="author">
          <h3>Challange by <a href="https://frontendmentor.io" target="_blank">Frontend Mentor</a> Coded by <a href="https://github.com/ArturHarutyunyan1" target="_blank">Artur Harutyunyan</a></h3>
      </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            result: []
        }
    },
    mounted(){
        this.generateAdvice()
    },
    methods:{
        generateAdvice(){
            fetch('https://api.adviceslip.com/advice')
            .then((res) => res.json())
            .then((data) => this.result = data)
        }
    }
}
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap');
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
    width: 500px;
    min-height: 300px;
    max-height: 100%;
    background: var(--dark-grayish-blue);
    border-radius: 15px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.adviceID{
    color: var(--neon-green);
    letter-spacing: 5px;
}

.advice{
    width: 90%;
    height: 115px;
    font-size: 28px;
    text-align: center;
    transform: translateY(20px);
    color: var(--light-cyan);
}

.divider{
    transform: translateY(55px);
}

.btn{
    width: 50px;
    height: 50px;
    background: var(--neon-green);
    transform: translateY(70px);
    border-radius: 50%;
    border: none;
    cursor: pointer;
    transition: 0.3s ease-out;
}

.btn:hover, .btn:focus{
    box-shadow: 0px 0px 20px 5px var(--neon-green);
}

.mobile{
    display: none;
}

.author{
    font-size: 12px;
    position: absolute;
    bottom: 10px;
    color: var(--light-cyan);
}

a{
    color: var(--neon-green);
    text-decoration: none;
}


@media (max-width: 500px){
    .card{
        width: 90%;
        height: 340px;
        margin: auto;
    }
    .advice{
        width: 100%;
        font-size: 28px;
    }
    .divider{
        transform: translateY(60px);
    }
    .btn{
        transform: translateY(73px);
    }
    .mobile{
        display: block;
    }
    .desktop{
        display: none;
    }
}
</style>