<template>

<div class="container">

<header>
       <h1>WE'RE LAUNCHING SOON</h1>
    </header>

     <main>
        <div class="timer">
          <div class="time-box" id="days">
            <div class="sheets">
                <div class="sheet top">
                   <p></p>
                   <div class="sheet front"><p> {{ days }} </p></div>
               </div>
                <div class="sheet bottom"><p> {{ days }} </p></div>
            </div>
            DAYS
         </div>
         <div class="time-box" id="hours">
          <div class="sheets">
            <div class="sheet top">
             <p></p>
             <div class="sheet front"><p> {{ hours }} </p></div>
          </div>
            <div class="sheet bottom"><p> {{ hours }} </p></div>
        </div>
            HOURS
         </div>
         <div class="time-box" id="minutes">
          <div class="sheets">
            <div class="sheet top">
             <p></p>
             <div class="sheet front"><p> {{ minutes }} </p></div>
         </div>
            <div class="sheet bottom"> 
               <p>  {{ minutes }} </p>
            </div>
        </div>
            MINUTES
         </div>
         <div class="time-box" id="seconds">
          <div class="sheets">
            <div class="sheet top">
             <p></p>
             <div class="sheet front"><p> {{ seconds }} </p></div>
         </div>
            <div class="sheet bottom"><p> {{ seconds }} </p></div>
        </div>
            SECONDS
         </div>
      </div>  
    </main>

     <footer>
      <nav>
         <a href="#" id="facebook-link"><img src="../assets/images/icon-facebook.svg" alt="facebook"></a>
         <a href="#" id="pinterest-link"><img src="../assets/images/icon-pinterest.svg" alt="pinterest"></a>
         <a href="#" id="instagram-link"><img src="../assets/images/icon-instagram.svg" alt="instagram"></a>
      </nav>
      <!-- <div class="attribution">
         <p> Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. </p>
         <p> Coded by <a href="https://github.com/wanlucas">Wan Lucas</a>. </p>
     </div> -->
   </footer>
</div>

</template>

<script>

export default {
  name: 'Count',
  


   data () {
    return {
      currentTime: 0,
      endTime: 'July 14, 2022 19:30:00',
      t: 0,
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0
    }
  },

  methods: {
    dateCounterTime () {
      this.currentTime = Date.parse(new Date())
      this.endTime = Date.parse(new Date(this.endTime))
      this.t = this.endTime - this.currentTime
      this.days = parseInt(this.t / (1000 * 60 * 60 * 24), 10)
      this.hours = parseInt((this.t / (1000 * 60 * 60)) % 24, 10)
      this.minutes = parseInt((this.t / 1000 / 60) % 60, 10)
      this.seconds = parseInt((this.t / 1000) % 60, 10)
      this.days = this.days < 10 ? '0' + this.days : this.days
      this.hours = this.hours < 10 ? '0' + this.hours : this.hours
      this.minutes = this.minutes < 10 ? '0' + this.minutes : this.minutes
      this.seconds = this.seconds < 10 ? '0' + this.seconds : this.seconds
    }

  },

  created () {
    setInterval(() => {
      this.dateCounterTime()
    }, 1000)

//      turnAnimation(local, value, txt, duration) {
//     local.style.animation = '', txt.classList = '';
//     setTimeout(()=> local.style.animation = `turn ${duration}s forwards`, 30);
//     setTimeout(()=> {txt.innerText = value-1, txt.classList = 'flip'}, (duration*1000) / 3);  
// }
  }

}



</script>

<style scoped>


/* body {
    display: flex;
    justify-content: center;
    background: black;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    font-family: 'Red Hat Text', sans-serif;
} */

.container {
    width: 100%;
    height: 100%;
    min-width: 260px;
    min-height: 350px;
    position: relative;
    background: hsl(0, 15%, 6%);
    background-image: url(../assets/images/bg-stars.svg);
    user-select: none;

}


header, nav, main {
    display: flex;
    align-items: center;
    justify-content: center;
}

header {
    height: 34vh;
    color: rgb(232, 232, 232);
    font-size: 0.55rem;
    font-weight: 700;
    letter-spacing: 0.4rem;
    text-shadow: 1px 0 hsla(0, 0%, 100%, 0.15);
}


main {
    width: 100%;
}


.timer {
    display: flex;
}

.time-box {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-size: 0.7rem;
    letter-spacing: 0.3rem;
    color: hsl(0, 0%, 57%);
    text-shadow: 1px 1px rgba(0, 0, 0, 0.15);
}
.sheets {
    width: 115px;
    height: 120px;
    background: hsla(0, 0%, 4%, 0.6);
    border-radius: 8px;
    margin: 13px;
}

.sheet {
    display: flex;
    justify-content: center;
    font-size: 4rem;
    height: 46%;
    font-weight: 700;
    color:hsl(345, 95%, 68%);
}
.sheet p {
    overflow: hidden;
    line-height: 0;
    opacity: 0;
    animation: fade 0.5s 1.2s forwards;
}

@keyframes fade {to {opacity: 1}}
.sheet.top p{
    display: flex;
    align-items: flex-end;
}
.sheet p.flip {
    display: flex;
    align-items: flex-start;
    transform: rotateX(180deg);
}
.sheet.top {
    position: relative;
    border-bottom: 1px solid transparent;
    background: hsl(234, 17%, 12%);
    border-radius: 6px 6px 0 0;
}

.sheet.top::after, .sheet.top::before {
    content: "";
    position: absolute;
    bottom: 0;
    right: 0;
    transform: translate(48%, 50%);
    background: hsl(0, 0%, 4%);
    height: 9px;
    width: 10px;
    border-radius: 50%;
    z-index: 20;
}
.sheet.top::before {
    right: unset;
    left: 0;
    transform: translate(-48%, 50%);
}
.sheet.bottom {
    position: relative;
    background: hsl(230, 15%, 16%);
    border-radius: 0 0 6px 6px;
    transform-style: preserve-3d;
}

.sheet.front {
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: inherit;
    border-radius: inherit;
    z-index: 10;
}

@keyframes turn {
    from {
        background: hsl(240, 11%, 23%);
    }
    to {
        background: hsl(230, 14%, 17%);
        transform: translateY(100%) rotateX(-180deg);
    }
}


footer {
    position: absolute;
    width: 100%;
    height: 23vh;
    bottom: 0;
    background-repeat: no-repeat;
    background-size: cover;
    background-image: url(../assets/images/pattern-hills.svg);
}
nav {
    width: 100%;
    height: 100%;
    padding-top: 2%;
}
nav a {
   margin: 0 12px;
}
nav a img {
    width: 1.2rem;
}
nav a img:hover {
    filter: brightness(2);
}

@media only screen and (max-width: 1300px) {
    .container {
        width: 100%;
    }
}
@media only screen and (max-width: 600px) {
    html {
        font-size: 75%;
    }
    .sheets {
        width: 80px;
        height: 84px;
        margin: 8px;
    }
    nav a img {
        width: 2rem;
    }
}
@media only screen and (max-width: 400px) {
    html {
        font-size: 50%;
    }
    .sheets {
        width: 60px;
        height: 63px;
        margin: 2px;
    }
}
@media only screen and (min-width: 1400px) {
    html {
        font-size: 120%;
    }
    .sheets {
        width: 140px;
        height: 145px;
        margin: 15px;
    }
}
</style>
