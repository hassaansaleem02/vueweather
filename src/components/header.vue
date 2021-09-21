 <template>
  <header class="navbar">
    <h3>VUE-JS Weather App</h3>
    <nav class="list">
      <ul>
        <li><a href="app.vue">Home</a></li>
        <li><a href="https://api.openweathermap.org">API</a></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
  
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap");

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 9px 1%;
}

h3 {
  font-family: "Bebas Neue";
  font-size: 25px;
  color: rgb(130 87 103);
}

li a {
  font-family: "Bebas Neue";
  text-decoration: none;
  font-size: 20px;
  color: rgb(130 87 103);
}

.list li {
  display: inline-block;
  list-style: none;
  padding: 0px 10px;
}
.list li a:hover {
  color: rgb(39, 24, 41);
  cursor: pointer;
}
</style>>

