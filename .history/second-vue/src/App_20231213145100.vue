<template>
 <div class="container">
    <h1 class="white-text">{{ formattedDate }}</h1>

    <div>
      <p class="white-text">
        Day: {{ newDay }}
        <span v-if="addedDay > 0" class="white-text">
          <template v-if="addedDay === 1"> (+ {{ addedDay }} day)</template>
          <template v-else> (+ {{ addedDay }} days)</template>
        </span>
      </p>
      <button @click="handleAddedDay">Add Days</button>
    </div>

    <div>
      <p class="white-text">
        Month: {{ newMonth }}
        <span v-if="addedMonth > 0" class="white-text">
          <template v-if="addedMonth === 1"> (+ {{ addedMonth }} month)</template>
          <template v-else> (+ {{ addedMonth }} months)</template>
        </span>
      </p>
      <button @click="handleAddedMonth">Add Months</button>
    </div>

    <div class="action-btn">
      <button @click="handleChangeDate" class="change-btn white-text" title="Click to set new date">
        Update Date
      </button>
      <button @click="handleReset" class="reset-btn white-text">Reset</button>
    </div>
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
    formattedDate() {
      return this.currentDate.toDateString();
    },
    newDay() {
      return this.addDay(this.addedDay).getDate();
    },
    newMonth() {
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
    handleChangeDate() {
      const resultDate = this.addMonth(this.addedMonth, this.addDay(this.addedDay));
      this.currentDate = resultDate;
    },
    handleReset() {
      this.currentDate = new Date();
      this.addedDay = 0;
      this.addedMonth = 0;
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
  color: white);
  background-color: #242424;
  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.container {
  background-color: #333; 
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center; 
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
}
.white-text {
  color: white;
}
body {
  min-width: 32rem;
  min-height: 100vh;
  font-size: 1.6rem;
  display: flex;
  place-items: center;
  justify-content: center;
  align-items: center;
}

h1 {
  font-size: 2.4rem;
  line-height: 1.1;
}

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

#app {
  padding: 2rem;
  text-align: center;
}

.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.action-btn {
  display: flex;
  gap: 2rem;
}

.action-btn {
  margin-top: 1rem; 
  display: flex;
  gap: 1rem;
  align-items: center; 
}

.change-btn {
  background-color: rgb(135, 36, 110);
}

.reset-btn {
  background-color: red;
}

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