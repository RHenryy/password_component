<template>
<div class="hero">
    <h2>{{ msg }}</h2><br>
     <div v-if="notEmpty" class="notification is-small is-danger ">Fields cannot be empty!</div>
     <div v-if="minLength" class="notification is-small is-danger ">Password must contain at least 8 characters!</div>
     <div v-if="validation === false" class="notification is-small is-danger ">Passwords do not match!</div>
    <div v-if="validation === true" class="notification is-small is-success ">Successfully register!</div>

    <section class="container"> 
    <b-field label="Password">
            <b-input @keydown.native.space.prevent 
              type="password"
              v-model="password"
              
                value=""
                password-reveal
                >
            </b-input>
        </b-field>
    </section><br/>
    <section class="container"> 
    <b-field label="Confirm password">
            <b-input @keydown.native.space.prevent 
            type="password"
            v-model="checkPassword"
                value=""
                password-reveal>
            </b-input>
        </b-field>
        <button @click="submitPassword()" class="button is-primary">Check password</button>
    </section>
    <div v-if="password.length >= 8" class="container">
        <div style="border-radius:45px;" class="notification is-danger mt-5" v-if="strengthPassword === 1"> Your password is weak!</div>
        <div style="border-radius:45px;" class="notification is-warning mt-5" v-if="strengthPassword === 2"> Your password is average!</div>
        <div style="border-radius:45px;" class="notification is-info mt-5" v-if="strengthPassword === 6"> Your password is stronger!</div>
        <div style="border-radius:45px;" class="notification is-success mt-5" v-if="strengthPassword === 8"> Your password is very strong!</div>
      </div>
      
       
       

   
    
    
   
 </div> 
</template>

<script>

export default {
  name: 'PasswordForm',
  props: {
    msg: String,
    
  },
  setup() {},
  data() {
    return {
    password:'',
    checkPassword:'',
    notEmpty:false,
    minLength: false,
    validation:'undefined',
    
    }},
    computed: {
      strengthPassword() {

            
         
            let variations = {
              hasNumber   : /\d/.test(this.password),
              hasLowercase : /[a-z]/.test(this.password),
              hasUppercase : /[A-Z]/.test(this.password),
              hasSpecial   : /[!@#$%^/&*)(+=._-]/.test(this.password) 
            };
            let variationNumber = 0;
            for (let check in variations)
            {
              
              variationNumber += (variations[check] === true);
              variationNumber += (variations['hasSpecial'] === true);
              
              
          }

            return variationNumber;
      }  },

      methods: {
      submitPassword(){
      if (this.password !== '' || this.checkPassword !== '')
      { 
         this.notEmpty = false;
         this.validation = 'undefined';
       
        if(this.password.length >= 8)
        {
          this.minLength = false;
          if(!this.minLength)
          {
             
             
                 
             
                    if(this.password === this.checkPassword)
                    {
                      this.validation = true;
                      this.password = '';
                      this.checkPassword ='';
                      
                
                

                    }  else return this.validation = false;
              
          

                  } 
            
                } else return this.minLength = true;
              } else return this.notEmpty = true;
            }, 

    
  }};
                 

         
        
        
      
      
      

   

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
</style>
