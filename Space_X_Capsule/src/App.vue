<template>
  <nav>
    <router-link to="/">Capsules</router-link> |
    <router-link to="/about">Details</router-link>
  </nav>
  <router-view/>
 
</template>




<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

ul{
padding-bottom: 30px;

}

li {

  padding-bottom: 10px;
  cursor: pointer;
  font-size:20px
}

li:hover {
  color: red;

}

a {
 text-decoration: none;

}

a:hover {
  color: red;

}

</style>
