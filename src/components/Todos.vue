<template>
    <div>
      <h1>Catatan Tugas</h1>
      <form>
        <label for="activity">Tugas:</label>
        <input type="text" id="activity" v-model="newActivity"><br><br>
        <button type="button" @click="addActivity">Tambah</button>
        <button type="button" @click="filterUnfinished">Filter Halaman</button>
      </form>
      <ul>
        <li v-for="(activity, index) in activities" :key="index" :style="{textDecoration: activity.completed ? 'line-through' : 'none'}">
          {{ activity.name }}
          <button @click="removeActivity(index)">Hapus</button>
          <button @click="completeActivity(index)" v-if="!activity.completed">Selesai</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        activities: [],
        newActivity: "",
      };
    },
    methods: {
      addActivity() {
        if (this.newActivity !== "") {
          this.activities.push({ name: this.newActivity, completed: false });
          this.newActivity = "";
        }
      },
      removeActivity(index) {
        this.activities.splice(index, 1);
      },
      completeActivity(index) {
        this.activities[index].completed = true;
      },
      filterUnfinished() {
        this.activities = this.activities.filter(function (activity) {
          return !activity.completed;
        });
      },
    },
  };
  </script>
  
  <style>
  body {
    background: url('/src/bground.jpeg') no-repeat center center fixed;
    background-size: cover;
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
  }
  
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
  }
  
  h1 {
    color: black;
    margin-top: 50px;
    text-align: center;
  }
  
  form {
    text-align: center;
  }
  
  label {
    display: inline-block;
    margin-right: 10px;
    text-align: right;
    width: 80px;
  }
  
  input[type="text"] {
    border: 2px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    font-size: 16px;
    margin: 5px 0;
    padding: 10px;
    width: calc(100% - 100px); /* Adjusted width */
  }
  
  button {
    background-color: rgb(252, 144, 203);
    border: none;
    border-radius: 4px;
    color: white;
    cursor: pointer;
    font-size: 16px;
    margin: 5px;
    padding: 10px 20px; /* Adjusted padding */
  }
  
  button:hover {
    background-color: #4b163f;
  }
  
  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
  }
  
  li {
    background-color: #d09ec9; /* Adjusted background color */
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-bottom: 5px;
    padding: 10px;
  }
  
  li button {
    background-color: #47183e;
    border: none;
    border-radius: 4px;
    color: white;
    cursor: pointer;
    font-size: 14px;
    margin-left: 5px;
    padding: 5px;
  }
  
  li button:last-child {
    background-color: #e75dd4;
  }
  
  li button:hover {
    background-color: #e60000;
  }
  
  li button:last-child:hover {
    background-color: #420d51;
  }
  
  li.completed {
    text-decoration: line-through;
  }
  </style>