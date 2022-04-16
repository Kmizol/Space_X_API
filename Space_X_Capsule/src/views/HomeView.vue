<template>
  <div class="home">
    <div>
      <p>
        <span class="active" style="padding : 0 10px 0 10px">Active</span>
        <span class="retired" style="padding : 0 10px 0 10px">Retired</span>
        <span class="unknown" style="padding : 0 10px 0 10px">Unknown</span>
        <span class="destroyed" style="padding : 0 10px 0 10px">Destroyed</span></p>
    </div>
    <h1>Liste des Capsules Space-X</h1>
    <div class="content">
    <ul v-for='capsule in capsule'
      :key='capsule._id'
      :id='capsule.capsule_serial'>
      <span v-if="capsule.status == 'active'">
      <li class="active" >
      <a href="{{capsule}}"></a>
      <a v-bind:href="'/about/?capsule='+capsule.capsule_serial+'&id='+capsule.capsule_id+'&details='+capsule.details+'&landings='+capsule.landings+'&original_launch='+capsule.original_launch+'&original_launch_unix='+capsule.original_launch_unix+'&reuse_count='+capsule.reuse_count+'&status='+capsule.status+'&type='+capsule.type+'&mission='+capsule.mission">
      {{ capsule.capsule_serial }}
     </a></li>
      </span>
      <span v-if="capsule.status == 'retired'">
      <li class="retired" >
      <a href="{{capsule}}"></a>
      <a v-bind:href="'/about/?capsule='+capsule.capsule_serial+'&id='+capsule.capsule_id+'&details='+capsule.details+'&landings='+capsule.landings+'&original_launch='+capsule.original_launch+'&original_launch_unix='+capsule.original_launch_unix+'&reuse_count='+capsule.reuse_count+'&status='+capsule.status+'&type='+capsule.type+'&mission='+capsule.mission">
      {{ capsule.capsule_serial }}
     </a></li>
      </span>
      <span v-if="capsule.status == 'unknown'">
      <li class="unknown" >
      <a href="{{capsule}}"></a>
      <a v-bind:href="'/about/?capsule='+capsule.capsule_serial+'&id='+capsule.capsule_id+'&details='+capsule.details+'&landings='+capsule.landings+'&original_launch='+capsule.original_launch+'&original_launch_unix='+capsule.original_launch_unix+'&reuse_count='+capsule.reuse_count+'&status='+capsule.status+'&type='+capsule.type+'&mission='+capsule.mission">
      {{ capsule.capsule_serial }}
     </a></li>
      </span>
      <span v-if="capsule.status == 'destroyed'">
      <li class="destroyed">
      <a href="{{capsule}}" ></a>
      <a class="destroyed" v-bind:href="'/about/?capsule='+capsule.capsule_serial+'&id='+capsule.capsule_id+'&details='+capsule.details+'&landings='+capsule.landings+'&original_launch='+capsule.original_launch+'&original_launch_unix='+capsule.original_launch_unix+'&reuse_count='+capsule.reuse_count+'&status='+capsule.status+'&type='+capsule.type+'&mission='+capsule.mission">
      {{ capsule.capsule_serial }}
     </a></li>
      </span>
    </ul>
    </div>
  </div>
</template>


<script>
import axios from "axios";
export default {
  data: () => ({
    capsule: null
  }),
  created() {
    axios.get("https://api.spacexdata.com/v3/capsules").then((result) => {
      this.capsule = result.data;
      console.log(result.data);
    })
  }
};
</script>


<style>
ul{
padding-bottom: 0px;
text-align: left;

}

li {
list-style-type: none;
  padding-bottom: 0px;
  cursor: pointer;
  font-size:20px;
  
}

li:hover {
  color: red;

}




a {
 text-decoration: none;
 color: rgb(0, 0, 0);
 
}


a:hover {
  color: red;

}

.content{
  margin-left: 44%;
  margin-right: 46%;
  
}

.active {
 border: solid;
  background: #8ee58e;
  text-align: center;
}



.retired {
border: solid;
  background: #ef9b8f;
  text-align: center;
}

.unknown {
border: solid;
  background: #00000049;
  text-align: center;
}

.destroyed {
  text-decoration: none;
  background: #000000;
  color: white;
  text-align: center;
  border: solid black;
}
</style>


