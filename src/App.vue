<script lang="ts">
import "./styles/style.css";
import Card from "./components/Card.vue";

export default {
  name: "App",
  components: {
    Card,
  },
  data: () => ({
    showDays: '0',
    showHours: '0',
    showMinutes: '0',
    showSeconds: '0',
  }),
  computed: {
    _seconds: () => 1000,
    _minutes() {
      return this._seconds * 60;
    },
    _hours() {
      return this._minutes * 60;
    },
    _days() {
      return this._hours * 24;
    }
  },
  mounted() {
    this.countRemaining();
  },
  methods: {
    countRemaining() {
      const timer = setInterval(() =>  {
        const now = new Date();
        const end = new Date(2023, 5, 4);

        const distance = end.getTime() - now.getTime();
        if (distance < 0 ) {
          clearInterval(timer);
          return;
        }

        const days = Math.floor((distance / this._days));
        const hours = Math.floor((distance % this._days) / this._hours);
        const minutes = Math.floor((distance % this._hours) / this._minutes);
        const seconds = Math.floor((distance % this._minutes) / this._seconds);

        this.showDays = days < 10 ? "0" + days.toString() : days.toString();
        this.showHours = hours < 10 ? "0" + hours.toString() : hours.toString();
        this.showMinutes = minutes < 10 ? "0" + minutes.toString: minutes.toString();
        this.showSeconds = seconds < 10 ? "0" + seconds.toString : seconds.toString();

      }, 1000);
    }
  }
};
</script>

<template>
  <div class="Container">
    <div class="mainCard">
      <h1>My Happy Birthday</h1>
      <h3>T - MINUS:</h3>
      <div class="cardGrid">
        <Card :number="showDays" description="Days" />
        <Card :number="showHours" description="Hours" />
        <Card :number="showMinutes" description="Minutes" />
        <Card :number="showSeconds" description="seconds" />
      </div>
    </div>
  </div>
</template>

<style>
.Container {
  display: flex;
  align-items: center;
  justify-content: center;

  width: 100vw;
  height: 100vh;
}
.mainCard {
  width: 1049px;
  height: 507px;
  background: rgba(9, 33, 67, 0.8);
  box-shadow: 24px 26px 4px -11px rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(10px);

  border-radius: 36px;

  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.mainCard h1 {
  font-weight: 250;
  font-size: 4.5rem;
  line-height: 135px;
  text-align: center;
  letter-spacing: 0.125em;

  color: #ffffff;
}

.mainCard h3 {
  font-style: normal;
  font-weight: 600;
  font-size: 32px;
  line-height: 48px;
  text-align: center;
  letter-spacing: 0.2em;

  color: #a5deff;
}

.cardGrid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 26px;
}
</style>
