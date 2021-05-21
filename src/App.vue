<template>
  <div class="container">
    <h1>Hello Vue</h1>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:@wght@300;400&display=swap');

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  font-family: 'Poppins', sans-serif;
}

.container{
  max-width: 800px;
  min-height: 400px;
  margin: 30px  auto;
  border: 3px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  overflow: auto;
  box-shadow: 5px 8px 10px 12px rgba(0,0,0, 0.8);
}

.btn{
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 20px;
  font-family: inherit;
}

</style>
