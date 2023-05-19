<template>
    <div class="register-page">
      <b-container>
        <h1>Register</h1>

        <div v-if="showAlert" class="alert success">
          <h2>Registeration successful !</h2>
        </div>

        <b-form @submit.prevent="visitorRegister" v-if="showForm">
          <b-form-group class="group-label" label="Personal Information">
            <b-row>
              <b-col cols="12">
                <b-form-group class="" label="Full Name">
                  <b-form-input v-model="form.full_name" placeholder="Full Name" required></b-form-input>
                </b-form-group>
              </b-col>              
            </b-row>
            <b-row>
              <b-col cols="6">          
                <b-form-group label="Gender">
                  <b-form-radio-group v-model="form.gender" required>
                    <b-form-radio value="1">Male</b-form-radio>
                    <b-form-radio value="2">Female</b-form-radio>
                  </b-form-radio-group>
                </b-form-group>
              </b-col>
              <b-col cols="6">
                <b-form-group label="Vehicle / Walk-in">
                  <b-form-radio-group v-model="form.vehicle_walk_in" required>
                    <b-form-radio value="1">Vehicle</b-form-radio>
                    <b-form-radio value="2">Walk-in</b-form-radio>
                  </b-form-radio-group>
                </b-form-group>
              </b-col>
            </b-row>
          </b-form-group>
          
          <b-form-group label="Contact Details">
            <b-row>
              <b-col cols="6">
                <b-form-group label="Email">
                    <b-form-input v-model="form.email" type="email" placeholder="Email" required></b-form-input>
                </b-form-group>
              </b-col>
              <b-col cols="6">
                <b-form-group label="Phone">
                  <b-form-input v-model="form.phone" placeholder="Phone" required></b-form-input>
                </b-form-group>
              </b-col>             
            </b-row>
          </b-form-group>                  

          <b-form-group label="Address">
            <b-form-textarea v-model="form.address" placeholder="Enter the Address ..." rows="3" required></b-form-textarea>
          </b-form-group>

          <b-form-group label="Purpose of Visit">
            <b-form-textarea v-model="form.visit_purpose" placeholder="Enter the purpose of your visit" rows="4" required></b-form-textarea>
          </b-form-group>
          
          <b-button variant="primary" @click="goBack"><i class="fa fa-arrow-circle-left fa-lg"></i>  Go Back</b-button>
          <b-button type="submit" variant="primary"><i class="fa fa-paper-plane" aria-hidden="true"></i> Submit</b-button>
        </b-form>
        
      </b-container>
    </div>
  </template>
  
  <script>
  import '@fortawesome/fontawesome-free/css/all.css';
  import { BootstrapVue } from 'bootstrap-vue';
 
  export default {
    name: 'RegisterPage',
    data() {
      return {
        showForm: true,
        showAlert: false,

        form: {          
          full_name: '',
          email: '',
          phone: '',
          address: '',
          vehicle_walk_in: '',
          gender: '',
          visit_purpose: '',
        },        
      };
    },
    methods: {
      visitorRegister() {        
        this.$axios.$post('visitor-register', this.form)
        .then((res) => {
          console.log(res);          
        });
        
        this.showAlert = true;
        this.showForm = false;    
        
        const interval = setInterval(() => {
          this.showAlert = false;
          clearInterval(interval);
          this.$router.push('/');
        }, 1000); 
        
      },
      dismissAlert() {
        this.alertVisible = false;
      },
      goBack() {
        // Navigate back to the home page
        this.$router.push('/');        
      }
    }
  }
  </script>
  
  <style scoped>
  .register-page {
    padding: 20px;
  }
  .group-label label {
    /* Add your custom CSS styles for the label here */
    font-weight: bold;
    color: #333;
    /*.. . */
    }
  .group-label label::after {
    content: '*';
    color: red;
    }
  .alert {
    background-color: #d4edda;
    color: #155724;
    padding: 10px;
    margin-top: 10px;
    display: none;
  }
  .alert.success {
    background-color: #dff0d8;
    color: #155724;
    display: block;
    margin-top: 3rem;
  }
</style>
  