<script>
  export default {
    data() {
      return {
        firstName: "Lorenzo",
        lastName: "Hajdari",
        email: "lory.h4000@gmail.com",
        gender: "male",
        picture: "https://lh3.google.com/u/0/d/1v7idvvJXeDyKYBlKSag-JZ-klJc84PYA=w1366-h657",
        location: {
          street: {
            number: 15,
            name: "Gian Battista Vico"
          },
          city: "Milano",
          state: "Lombardia",
          country: "Italy"
        }
      }
    },

    methods: {
      async getUser() {
        const res = await fetch('https://randomuser.me/api')
        const { results } = await res.json()

        this.firstName = results[0].name.first
        this.lastName = results[0].name.last
        this.email = results[0].email
        this.gender = results[0].gender
        this.picture = results[0].picture.large
        this.location.street.number = results[0].location.street.number
        this.location.street.name = results[0].location.street.name
        this.location.city = results[0].location.city
        this.location.state = results[0].location.state
        this.location.country= results[0].location.country
      }
    }
  }
</script>

<template>
  <div class="card" :style="{ backgroundImage: 'url(' + picture + ')'}">
    <div class="border" :id="gender">
      <h1>USER INFO</h1>
      <hr>
      <p>Full name: {{firstName}} {{lastName}}</p>
      <p>Email: {{email}}</p>
      <p>Gender: {{gender}}</p>
      <p>Location: {{location.street.number}}, {{location.street.name}} Street ({{location.city}}, {{location.state}}, {{location.country}})</p>
    </div>
  </div>
  <button @click="getUser">Change User</button>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;400&display=swap');

* {
  font-family: 'Poppins', sans-serif;
  font-weight: 100;
  
}
body {
  margin: 0;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.border {
    height: 100%;
    width: 100%;
    border-radius: 10px;
    background: transparent;
    transition: 1s;
    position: absolute;
    text-align: justify;
    top: 0;
    bottom: 0;

}

#male:hover {
    background: rgb(74, 74, 243);
}

#female:hover {
  background: rgb(248, 39, 74);
}


.card {
  height: 300px;
  width: 300px;
  text-align: left;
  transition: 0.8s;
  overflow: hidden;
  border-radius: 10px;
  background-size: 300px;
  background-repeat: no-repeat;
  background-position: center center;
  position: relative;

}

.card:hover {
    background-repeat: no-repeat;
    background-position: left center;
    background-size: 600px;
}

.card:hover p {
    opacity: 1;
}

.card:hover h1 {
    opacity: 1;
}

.card:hover hr {
  opacity: 1;
}

hr {
  opacity: 0;
  width: 80%;
  margin-bottom: 20px;
  transition: opacity 1s;
}

h1 {
  font-size: 20px;
  margin: 30px 10% 15px 10%;
  letter-spacing: 3px;
  color: white;
  text-align: center;
  font-weight: 400;
  opacity: 0;
  transition: opacity 1s;
}

p {
    font-size: 15px;
    color: white;
    opacity: 0;
    margin: 0 10%;
    transition: opacity 1s;
}

button {
    padding: 15px 35px;
    font-size: 15px;
    margin-top: 20px;
    outline: none;
    border: 1px solid #333;
    background: transparent;
    color: black;
    font-weight: 400;
    cursor: pointer;
}

</style>
