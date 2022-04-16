<script>
import axios from "axios";

export default {

  data: () => ({

    launches: null

  }),

  created() {

    axios.get("https://api.spacexdata.com/v3/launchpads/").then((result) => {

      this.launches = result.data;

      console.log(result.data);
      
      console.log(window.location.pathname);

    })

  }

};
</script>


<template>
  <div id="app">
    <div v-for="launch in launches"
      :key="launch">
      
        <div v-if="launch.status == 'active'">
          <div>
            <b>Launch name:</b> {{launch.name}}
          </div>
          <div>
            <b>Status:</b>   {{launch.status}}
          </div>
          <div>
            <b>Location:</b>   {{launch.location}}
          </div>
          <div>
            <b>Successful_launches:</b>   {{launch.successful_launches}}
          </div>
        </div>
        <div v-else>
            <span class="retired">
                <div>
                    <b>Launch name:</b> {{launch.name}}
                </div>
                <div>
                    <b>Status:</b>   {{launch.status}}
                </div>
                <div>
                    <b>Location:</b>   {{launch.location}}
                </div>
                <div>
                    <b>Successful_launches:</b>   {{launch.successful_launches}}
                </div>
            </span>
        </div>
        <br>
      

      
    </div>
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
