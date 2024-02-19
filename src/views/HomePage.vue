<template>
  <div class="container">
    <h1>{{ name }}</h1>
    <button @click="getData()" class="btn btn-success">Get Data</button>
    <div v-if="loadingStatus">
      <div class="spinner-border text-primary" role="status">
        <span class="visually-hidden">Loading...</span>
      </div>
    </div>

    <table class="table table-hover text-start">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Image</th>
          <th scope="col">Category</th>
          <th scope="col">Price</th>
        </tr>
      </thead>
      <tbody>
        <tr v-if="posts.length == 0" class="text-center">
          <th scope="row" colspan="4">There is no data</th>
        </tr>
        <tr v-else v-for="(p, index) in posts" :key="index">
          <th scope="row">{{ p.id }}</th>
          <td>
            <img
              style="width: 100px"
              class="img img-thumbnail"
              :src="p.image"
              alt=""
            />
          </td>
          <td>{{ p.category }}</td>
          <td>$ {{ p.price }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HomePage",
  data() {
    return {
      name: "Home Page",
      loadingStatus: false,
      posts: [],
    };
  },
  methods: {
    getData() {
      this.loadingStatus = true;
      fetch("https://fakestoreapi.com/products")
        .then((res) => res.json())
        .then((json) => {
          this.posts = json;
          this.loadingStatus = false;
        });
    },
  },
};
</script>

<style lang="stylus" scoped></style>
