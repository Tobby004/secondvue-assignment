<template>
  <div class="app">
    <h1>{{ newdate }}</h1>

    <div>
      <p>
        Day: {{ newDay }}
        <span v-if="addedDay > 0">
          <template v-if="addedDay === 1"> (+ {{ addedDay }} day)</template>
          <template v-else> (+ {{ addedDay }} days)</template>
        </span>
      </p>
      <button @click="handleAddedDay">Add Days</button>
    </div>

    <div>
      <p>
        Month: {{ newMonth }}
        <span v-if="addedMonth > 0">
          <template v-if="addedMonth === 1"> (+ {{ addedMonth }} month)</template>
          <template v-else> (+ {{ addedMonth }} months)</template>
        </span>
      </p>
      <button @click="handleAddedMonth">Add Months</button>
    </div>

    <div class="action-btn">
      <button @click="handleChangeDate" class="change-btn" title="Click to set new date">
        Change The World!
      </button>
      <button @click="handleReset" class="reset-btn">Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      date: new Date(),
      addedDay: 0,
      addedMonth: 0,
      newdate: new Date().toString(),
    };
  },
  methods: {
    addDay(numberOfDays, baseDate = this.date) {
      const newDate = new Date(baseDate);
      newDate.setDate(newDate.getDate() + numberOfDays);
      return newDate;
    },
    addMonth(numberOfMonths, baseDate = this.date) {
      const newDate = new Date(baseDate);
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
      this.newdate = resultDate.toString();
    },
    newMonth() {
      return this.addMonth(this.addedMonth).getMonth() + 1;
    },
    newDay() {
      return this.addDay(this.addedDay).getDate();
    },
    handleReset() {
      this.newdate = this.date.toString();
      this.addedDay = 0;
      this.addedMonth = 0;
    },
  },
};
</script>

<style scoped>
/* Add your CSS styles here */
</style>