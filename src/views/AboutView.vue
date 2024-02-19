<template>
  <div>This is About</div>
</template>

<script>
import axios from "axios";
export default {
  name: "AboutView",
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
      .get("http://localhost:3000/posts")
      .then((response) => {
        console.log(response.data);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
