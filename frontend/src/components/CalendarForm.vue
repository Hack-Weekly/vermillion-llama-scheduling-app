<template>
  <div class="event-form-container">
    <form @submit.prevent="submitForm" class="event-form">
      <div class="form-group">
        <label for="eventName">Event Name:</label>
        <input type="text" id="eventName" v-model="eventName" required />
      </div>

      <div class="form-group">
        <label for="timeOptions">Times that might work:</label>
        <textarea id="timeOptions" v-model="timeOptions"></textarea>
      </div>

      <div class="form-group">
        <label>Time Range:</label>
        <div class="time-selector">
          <label for="startTime">Start Time:</label>
          <input type="time" id="startTime" v-model="startTime" required />
        </div>
        <div class="time-selector">
          <label for="endTime">End Time:</label>
          <input type="time" id="endTime" v-model="endTime" required />
        </div>
      </div>

      <div class="form-group">
        <label for="dateOptions">Dates that might work:</label>
        <textarea id="dateOptions" v-model="dateOptions"></textarea>
      </div>

       <div class="form-group">
      <label for="selectedDate">Select a Date:</label>
      <v-date-picker
        v-model="selectedDate"
        :mode="'single'"
        :show-calendar-on-focus="true"
      ></v-date-picker>
    </div>

      <div class="form-group">
        <button type="submit" class="submit-button">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
import { VDatePicker } from "v-calendar";

export default {
  components: {
    VDatePicker,

  },
  data() {
    return {
      eventName: "",
      timeOptions: "",
      startTime: "",
      endTime: "",
      dateOptions: "",
      selectedDate: null,
    };
  },
  methods: {
    submitForm() {
      // Handle form submission here, e.g., collect form data and send it to the server
      const formData = {
        eventName: this.eventName,
        timeOptions: this.timeOptions,
        startTime: this.startTime,
        endTime: this.endTime,
        dateOptions: this.dateOptions,
        selectedDate: this.selectedDate,
      };

      // Example: Send formData to the server or perform further processing
      console.log(formData);
    },
  },
};
</script>

<style scoped>
.event-form-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.event-form {
  width: 80%;
  max-width: 600px;
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
}

textarea {
  width: 100%;
  height: 100px;
}

.time-selector {
  display: flex;
  justify-content: space-between;
}

.submit-button {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  margin-top: 20px;
}

.submit-button:hover {
  background-color: #0056b3;
}
</style>
