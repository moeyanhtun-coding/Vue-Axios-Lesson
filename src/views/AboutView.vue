<template>
  <div class="container">
    <h1>This is Lists Data From Json-Server</h1>
    <div class="row">
      <div class="col-4">
        <div class="row mb-2">
          <p class="col-2">Title</p>
          <input
            v-model="title"
            type="text"
            class="form-control col offset-1"
          />
        </div>
        <div class="row mb-2">
          <p class="col-2">Description</p>
          <textarea
            v-model="description"
            name=""
            id=""
            cols="20"
            rows="8"
            class="form-control col offset-1"
          ></textarea>
        </div>
        <div class="row mb-2">
          <p class="col-2">View</p>
          <input
            v-model="view"
            type="number"
            class="form-control col offset-1"
          />
        </div>
        <div class="row">
          <button @click="saveData()" class="col-3 offset-3 btn btn-primary">
            Save
          </button>
        </div>
      </div>
      <div class="col-8">
        <div class="card mb-2" v-for="(list, index) in lists" :key="index">
          <div class="card-header">{{ list.title }}</div>
          <div class="card-body">
            <h5 class="card-title">{{ list.views }}</h5>
            <p class="card-text">
              {{ list.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "AboutView",
  data() {
    return {
      lists: [],
      title: "",
      view: "",
      description: "",
    };
  },
  methods: {
    saveData() {
      let myData = {
        id: "100",
        title: this.title,
        description: this.description,
        view: this.view,
      };
      console.log(myData);
    },
  },
  mounted() {
    // axios
    //   .get("http://localhost:3000/posts")
    //   .then(function (response) {
    //     // handle success
    //     console.log(response.data);
    //   })
    //   .catch(function (error) {
    //     // handle error
    //     console.log(error);
    //   });
    axios
      .get("http://localhost:3000/posts  ")
      .then((response) => {
        this.lists = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
