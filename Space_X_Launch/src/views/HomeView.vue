
<script>
import axios from "axios";

export default {

  data: () => ({

    launches: null

  }),

  created() {

    axios.get("https://api.spacexdata.com/v3/launchpads").then((result) => {

      this.launches = result.data;

      console.log(result.data);
      
      console.log(window.location.pathname);

      

    })

  }

};
</script>

<template>
  <div id="app">
    <ul v-for="launch in launches"
      :key="launch">
      <span v-if="launch.status == 'active'">
        <li  class="active">
          
          <a href="{{launch.id}}"></a>
          <a v-bind:href="'DetailsView.vue?name='+launch.id">{{launch.name}}</a>
        </li>
      </span>
      <span v-else>
        <li class="retired">
          
          <a href="{{launch.id}}"></a>
          <a v-bind:href="'DetailsView.vue?name='+launch.id">{{launch.name}}</a>
        
        </li>
      </span>
    </ul>
  </div>
</template>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


.active {
  background: #8ee58e;
}

.retired {
  background: #ef9b8f;
}

</style>
