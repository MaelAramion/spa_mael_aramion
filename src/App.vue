<template lang="jade">
  <div id="app">
    <nav>
      <router-link to="/home">Home</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<script>
// import HelloWorld from "@/components/HelloWorld";
//
// export default {
//   components : {
//     HelloWorld
//   }
// }
</script>

<style>
body{
  background: #e1b12c;
  color : aliceblue;
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif, monospace;
  margin: 0;
  padding: 0;
}

nav {
  padding: 30px;
  text-align: center;
  background: #fbc531;
  margin: 0;
}

nav a {
  font-weight: bold;
  color: white;
  text-decoration: none ;
  font-size: 2em;
}

nav a.router-link-exact-active {
  color: #273c75;

}
nav a:hover{
  color: #273c75;
}
</style>
