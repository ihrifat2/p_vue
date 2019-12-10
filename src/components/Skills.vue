<template>
  <div class="hello">
    <div class="holder">
      <form action="" @submit.prevent="addSkill">
        <input type="text" placeholder="Enter a skill..." v-model="skill" v-validate="'min:5'" name="skill">
        <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
      </form>
      <ul>
        <li v-for="(data, index) in skills" :key='index'>{{ index+1 }}.{{ data.skill }}</li>
        <p v-if="skills.length >= 1">You have {{ skills.length }} skills</p>
        <p v-else>You have less than or equal to 1 skill</p>
        <div v-bind:class="alertObject"></div>
        <div v-bind:style="{ backgroundColor: bgColor, width:bgWidth, height: bgHeight }"></div>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skill:'',
      skills: [
        {"skill": "Vue.js"},
        {"skill": "NodeJS"},
        {"skill": "ReactJs"},
      ],
      alertObject: {
        alert: true,
        anotherclass: true
      },
      bgColor: 'yellow',
      bgWidth: '100%',
      bgHeight: '30px'
    }
  }, 
  methods: {
    addSkill() {
      this.skills.push({skill: this.skill})
      this.skill = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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

  input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7F;
  }
  .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }
</style>
