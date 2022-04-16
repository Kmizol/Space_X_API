<template>
 
    <h1>Détail Capsule</h1>
  <div class="about">
    <ul class="listdetail">
      <li class="detail gris"><b>Capsule_id :</b>.................................. {{ $route.query.id }}</li>
      <li class="detail"><b>Capsule_serial : </b>........................... {{ $route.query.capsule }} </li>
      <li class="detail gris"><b>Details :</b>.......................................... {{ $route.query.details }}</li>
      <li class="detail"><b>Landings : </b>..................................... {{ $route.query.landings }} </li>
      <li class="detail gris"><b>Original_launch :</b>........................... {{ $route.query.original_launch }}</li>
      <li class="detail"><b>Original_launch_unix :</b>.................. {{ $route.query.original_launch_unix }}</li>
      <li class="detail gris"><b>Reuse_count: </b>................................ {{ $route.query.reuse_count }}</li>
      <li class="detail"><b>Status : </b>........................................... {{ $route.query.status }}</li>
      <li class="detail gris"><b>Type : </b>.............................................. {{ $route.query.type }}</li>
    </ul>
   
  </div>
</template>


<script>
import axios from "axios";
export default {
  data: () => ({
    capsule: null
  }),
  created() {
    axios.get(`https://api.spacexdata.com/v3/capsules/`).then((result) => {
      this.capsule = result.data;
      console.log(result.data);
    })
  }
};
</script>


<style>
.about{
  padding-top: 100px  ;
}

.listdetail{

}

.detail{
  font-size: 30px;
  padding : 10px 0 10px 0;
  
  
}

.gris {

  background-color: rgba(0, 0, 0, 0.116);
}

.center{
text-align:center;

}

</style>