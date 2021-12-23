<template>
  <div class="hello">
    <h1>{{ personalDetails.name }}</h1>
    <div class="space-between">
      <div>
        {{ personalDetails.dob }} 
      </div>
      <div>
        {{ email }}
      </div>
    </div>
    <div class="p-5">{{ personalDetails.about }}</div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    email: String,
    personalDetails: Object,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.hello {
  width: 80%;
  box-shadow: 5px 5px 5px lightgray;
  padding: 5px;
  margin: 1rem auto;
}

.space-between {
  display: flex;
  justify-content: space-between;
  color: gray;
  padding: 1rem;
}
</style>
