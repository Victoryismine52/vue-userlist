<template>
  <div class="container">
     <form @submit.prevent="addUser">
      <input type="text" placeholder="Enter your First name" v-model="User.FirstName"> 
      <input type="text" placeholder="Enter your Last name" v-model="User.LastName">
      <button type="submit">Add User</button>
      <br>
     </form>

    <div class="holder">
      <ul>
        <li v-for="(Users, index) in Users" :key='index'>{{Users.FirstName}} {{Users.LastName}}</li>
      </ul>
      <p>These are users of the system.</p>
      <div v-bind:class="{ alert: showAlert}"></div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'Users',
  data() {
    return {
      User: {FirstName: '', LastName: ''}, 
      Users: [
          { FirstName: "Bryan", LastName: "Nelson" },
          { FirstName: "Steve", LastName: "Smith" },
          { FirstName: "Frank", LastName: "Adams" }
      ],
      }
    },
    methods : {
      addUser(){
        this.Users.push({FirstName: this.User.FirstName, LastName: this.User.LastName});
        this.User.FirstName = '';
        this.User.LastName = '';
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7F;
  }

  .holder {
    background: #fff;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }
</style>
