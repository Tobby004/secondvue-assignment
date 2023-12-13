<template>
  <div class="app">
    <h1>{{ currentDate }}</h1>

    <div>
      <p>
        Day: {{ currentDay }}
        <span v-if="addedDay > 0">
          <template v-if="addedDay === 1"> (+ {{ addedDay }} day)</template>
          <template v-else> (+ {{ addedDay }} days)</template>
        </span>
      </p>
      <button @click="handleAddedDay">Add Days</button>
    </div>

    <div>
      <p>
        Month: {{ currentMonth }}
        <span v-if="addedMonth > 0">
          <template v-if="addedMonth === 1"> (+ {{ addedMonth }} month)</template>
          <template v-else> (+ {{ addedMonth }} months)</template>
        </span>
      </p>
      <button @click="handleAddedMonth">Add Months</button>
    </div>

    <!-- The rest of your component's template -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentDate: new Date(),
      addedDay: 0,
      addedMonth: 0,
    };
  },
  computed: {
    currentDay() {
      return this.addDay(this.addedDay).getDate();
    },
    currentMonth() {
      return this.addMonth(this.addedMonth).getMonth() + 1;
    },
  },
  methods: {
    addDay(numberOfDays) {
      const newDate = new Date(this.currentDate);
      newDate.setDate(newDate.getDate() + numberOfDays);
      return newDate;
    },
    addMonth(numberOfMonths) {
      const newDate = new Date(this.currentDate);
      newDate.setMonth(newDate.getMonth() + numberOfMonths);
      return newDate;
    },
    handleAddedDay() {
      this.addedDay += 1;
    },
    handleAddedMonth() {
      this.addedMonth += 1;
    },
  },
};
</script>


<style scoped>
:root {
  font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;
  color-scheme: light dark;
  color: rgba(255, 255, 255, 0.87);
  background-color: #242424;
  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Global styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* HTML styles */
html {
  /* 1rem = 10px(62.5%) */
  font-size: 62.5%;
}

/* Body styles */
body {
  min-width: 32rem;
  min-height: 100vh;
  font-size: 1.6rem;
  display: flex;
  place-items: center;
  justify-content: center;
  align-items: center;
}

/* Heading styles */
h1 {
  font-size: 2.4rem;
  line-height: 1.1;
}

/* Button styles */
button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6rem 1.2rem;
  margin-top: 0.4rem;
  font-size: 1.2rem;
  font-weight: 500;
  font-family: inherit;
  background-color: blue;
  cursor: pointer;
  transition: border-color 0.25s;
}

button:hover {
  border-color: #646cff;
}

button:focus,
button:focus-visible {
  outline: 4px auto -webkit-focus-ring-color;
}

/* App container styles */
#app {
  padding: 2rem;
  text-align: center;
}

/* .app styles */
.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

/* .action-btn styles */
.action-btn {
  display: flex;
  gap: 2rem;
}

.action-btn > button {
  width: 14rem;
  height: 3.2rem;
}

/* .change-btn styles */
.change-btn {
  background-color: green;
}

/* .reset-btn styles */
.reset-btn {
  background-color: red;
}

/* Media query for light color scheme */
@media (prefers-color-scheme: light) {
  :root {
    color: #213547;
    background-color: #ffffff;
  }

  button {
    background-color: #f9f9f9;
  }
}
</style>