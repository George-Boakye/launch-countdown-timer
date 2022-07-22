<template>
  <div class="background">
    <figure class="bgimage-1">
      <img src="./assets/bg-stars.svg" alt="" />
    </figure>
    <figure class="bgimage-2">
      <img src="./assets/pattern-hills.svg" alt="" />
    </figure>
    <h1 class="header-text">We’re launching soon</h1>
    <div class="container">
      <div class="wrapper">
        <div class="card">
          <div class="card-top"></div>
          <div class="card-bottom">
            <p class="time">{{ days }}</p>
          </div>
        </div>
        <span>DAYS</span>
      </div>
      <div class="wrapper">
        <div class="card">
          <div class="card-top"></div>
          <div class="card-bottom">
            <p class="time">{{ formatTime(hours) }}</p>
          </div>
        </div>
        <span>HOURS</span>
      </div>
      <div class="wrapper">
        <div class="card">
          <div class="card-top"></div>
          <div class="card-bottom">
            <p class="time">{{ formatTime(minutes) }}</p>
          </div>
        </div>
        <span>MINUTES</span>
      </div>
      <div class="wrapper">
        <div class="card">
          <div class="card-top"></div>
          <div class="card-bottom">
            <p class="time">{{ formatTime(seconds) }}</p>
          </div>
        </div>
        <span>SECONDS</span>
      </div>
    </div>
    <div class="socials">
      <img src="./assets/icon-facebook.svg" alt="" />
      <img src="./assets/icon-instagram.svg" alt="" />
      <img src="./assets/icon-pinterest.svg" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      days: null,
      hours: null,
      minutes: null,
      seconds: null,
    };
  },
  mounted() {
    this.countdown();
    setInterval(this.countdown, 1000);
  },
  computed: {
    formatTime() {
      return (time) => {
        return time < 10 ? `0${time}` : time;
      };
    },
  },
  methods: {
    countdown() {
      const newYear = "1 Jan 2023";
      const newYearDate = new Date(newYear);
      const currentDate = new Date();
      const totalSeconds = (newYearDate - currentDate) / 1000;

      this.days = Math.floor(totalSeconds / 3600 / 24);
      this.hours = Math.floor(totalSeconds / 3600) % 24;
      this.minutes = Math.floor(totalSeconds / 60) % 60;
      this.seconds = Math.floor(totalSeconds % 60);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: "Red Hat Text", sans-serif;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.background {
  background-color: hsl(235, 16%, 14%);
  position: absolute;
  height: 100vh;
  width: 100%;
  z-index: -1;
  color: white;
  display: flex;
  flex-direction: column;
  // justify-content: center;
  align-items: center;
}
.bgimage-1 {
  position: absolute;
  top: 0;
  z-index: -1;
}
.bgimage-2,
.bgimage-2 img {
  position: absolute;
  bottom: 0;
  width: 100%;
  z-index: -1;
}
.container {
  display: flex;
  justify-content: space-between;
  width: calc(100% - 752px);
}
.wrapper {
  width: 148px;
}
.card {
  margin-bottom: 26px;
}
.card-top {
  background: #343650;
  opacity: 0.8;
  border-radius: 8px;
  height: 70px;
  width: 100%;
}
.card-bottom {
  background: #343650;
  border-radius: 8px;
  height: 70px;
  width: 100%;
  box-shadow: 0 12px 0px 0 rgba(25, 26, 35, 1);
}
hr {
  background: #000000;
  mix-blend-mode: normal;
  opacity: 0.25;
}
span {
  display: block;
  font-family: "Red Hat Text";
  font-style: normal;
  font-weight: 700;
  font-size: 14px;
  line-height: 19px;
  text-align: center;
  letter-spacing: 5.91875px;
  color: #8385a9;
}
.time {
  font-family: "Red Hat Text";
  font-style: normal;
  font-weight: 700;
  font-size: 80px;
  line-height: 71px;
  text-align: center;
  letter-spacing: -2.4px;
  color: #fb5e84;
  position: relative;
  top: -35px;
}
.header-text {
  margin-top: 132px;
  font-family: "Red Hat Text";
  font-style: normal;
  font-weight: 700;
  font-size: 22px;
  line-height: 29px;
  text-align: center;
  letter-spacing: 7.5px;
  text-transform: uppercase;
  margin-bottom: 104px;
  color: #ffffff;
}
.socials {
  position: absolute;
  bottom: 72px;
}
.socials img {
  margin-right: 32px;
}

@media screen and (max-width: 768px) {
  .background {
    overflow: hidden;
  }
  .header-text {
    font-family: "Red Hat Text";
    font-style: normal;
    font-weight: 700;
    font-size: 18px;
    line-height: 24px;
    text-align: center;
    letter-spacing: 6.13636px;
    text-transform: uppercase;
    color: #ffffff;
  }
  .w {
    width: calc(100% - 48px);
  }
  .card-top,
  .card-bottom {
    height: 33px;
    width: 70px;
  }
  .time {
    font-family: "Red Hat Text";
    font-style: normal;
    font-weight: 700;
    font-size: 36px;
    line-height: 71px;
    display: flex;
    align-items: center;
    text-align: center;
    letter-spacing: -1.08px;
    color: #fb5e84;
    left: 15px;
  }
  span {
    font-family: "Red Hat Text";
    font-style: normal;
    font-weight: 700;
    font-size: 7px;
    line-height: 9px;
    text-align: center;
    letter-spacing: 2.95937px;
    color: #8385a9;
  }
}
</style>
