<template>
  <f7-page>
    <f7-navbar sliding title="Home"></f7-navbar>
    <f7-block-title>{{ title }}</f7-block-title>
    <f7-block inner>
    
      <f7-list-item>
      <f7-label>email</f7-label>
      <f7-input type="text" :value="email" @input="email = $event.target.value" placeholder="Your email" clear-button></f7-input>
    </f7-list-item>
      <f7-list-item>
      <f7-label>password</f7-label>
      <f7-input type="text" :value="password" @input="password = $event.target.value" placeholder="Your password" clear-button></f7-input>
    </f7-list-item>
<p><f7-button fill color="red" @click="enter">enter</f7-button></p>
    </f7-block>
  </f7-page>
</template>
<script>
import firebase from 'firebase'
export default {
  name: 'Home',
  data() {
    return {
      title: 'Hello World',
      email:'',
      password:''
    };
  },
  methods:{
    enter(){
     
      firebase.auth().createUserWithEmailAndPassword(this.email,this.password).then((data)=>{
console.log('the data is ',data)
      }).catch(err=>{
        console.log(err)
      })
    }
  }
};
</script>
