<template>
  <div id="app">
   <div v-if="!logged" class="container">
      <!--Login -->
      <img src="./assets/logoStack.png" alt="Logo Stackoverflow" class="img-login" height="100" width="100">
      <form id="signin" class="form-signin">
        <h2 class="form-signin-heading">Stackoverflow</h2>
        <h4 class="form-signin-heading" style="padding-bottom: 15px;">Please sign in</h4>
        <label for="inputEmail" class="sr-only">Email address</label>
        <input type="email" id="inputEmail" class="form-control" placeholder="Email address" name="email" v-model="user.email" required autofocus>
        <label for="inputPassword" class="sr-only">Password</label>
        <input type="password" id="inputPassword" class="form-control" placeholder="Password" name="password" v-model="user.password" required>
        <button @click.prevent="signin" class="btn btn-lg btn-primary btn-block" data-dismiss="alert">Sign in</button>
        <!--<button class="btn btn-lg btn-success btn-block" data-toggle="modal" data-target="#exampleModal">Sign up</button>-->
        <b-btn v-b-modal.modalSignUp class="btn btn-lg btn-block" variant="success">Sign up</b-btn>
      </form>
       <!--Fin Login -->
    </div> <!-- /container -->
   
    <!-- Inicio   -->
    <div  v-if="logged"> 
      <div class="blog-masthead">
        <div class="container">
          <nav class="nav blog-nav">
            <img src="./assets/logoNavbar.png" alt="Logo Stackoverflow" height="50" width="auto">
            <a class="nav-link active" style="margin-left:30px;" href="#">Questions</a>
            <a class="nav-link" href="#">New Question</a>
            <a v-if="!logged" class="nav-link" href="#">Login</a>
            <a v-if="logged" class="nav-link" @click.prevent="signout" href="#">Logout</a>
              <!--<form class="form-inline">
                <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
                <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
                <button class="btn btn-outline-success my-2 my-sm-0" type="button">Login</button>
              </form>  -->
            <!--<b-btn v-b-modal.signinModal class="btn btn-outline-success my-2 my-sm-0">Sign In</b-btn>-->
          </nav>
        </div>
      </div>
      
      <!-- Create Question -->
      <div v-if="logged"class="row ask-question">
        <div class="container container-question">
          <div class="col-md-12">
            <form id="createQuestionForm">
              <h5 class="ask-something">{{ user.firstname }}, do you want to ask something?</h5>
              <div class="form-group">
                <!--<label for="exampleFormControlTextarea1">{{ user.firstname }}, do you want to ask something?</label>-->
              
                <textarea name="text" class="form-control" id="exampleFormControlTextarea1" v-model="question.text" rows="3" required></textarea>
              </div>
              <!-- <input class="btn btn-secondary btn-sm btn-color" type="button" value="Post">  -->
              <div class="btn-div">
                <button @click.prevent="createQuestion" class="btn btn-md btn-color">Post</button>
              </div>
            </form>
          </div>
        </div>
      </div>
      <!-- ./ Create Question -->

      <div class="container">
        
        <div class="row">
          <ul>
            <li class="questions-border" v-for="question in questions" :key="question._id">
              <div class="col-sm-12 blog-main">
                <div class="blog-post">
                 <!-- <h2 class="blog-post-title">Sample blog post</h2> -->
                  <p><b>¿? - </b> {{ question.text }}</p>
                  <p class="blog-post-meta">{{ question.author.firstname }} {{ question.author.lastname }} - <a href="#">{{ question.author.email }}</a>{{ question.createdAt }}</p>
                  <hr>
                  <div class="answers-div">
                    <ul style="list-style: none;">
                        <div class="list-group">
                          <!-- Answer li -->
                          <li class="answers-li" v-for="item in question.answers" :key="item._id">
                            <div  class="list-group-item list-group-item-action flex-column align-items-start">
                              <div class="d-flex w-100 justify-content-between">
                                <!--<h6 class="mb-1">{{ answer.author.firstname }} {{ answer.author.lastname }} - <a href="#">{{ answer.author.email }}</a> </h6>-->
                                <small>{{ item.createdAt }}</small>
                              </div>
                              <p class="mb-1">{{ item.text }}</p>
                            </div>
                          </li>
                          <!-- /.Answer li -->
                        </div>
                    </ul>
                  </div>
                  
                  <form v-if="logged" :id="question._id">
                    <input type="hidden" name="question" :value="question._id">
                    <div class="form-group">
                      <!-- <label for="exampleFormControlTextarea1">Example textarea</label> -->
                      <textarea class="form-control" name="text" rows="3" required></textarea>
                    </div>
                    
                    <button @click.prevent="createAnswer"  class="btn btn-secondary btn-sm btn-color">Reply</button>
                    
                  </form>
                  
                </div><!-- /.blog-post -->
              </div><!-- /.blog-main -->
            </li> <!-- /. li Questions -->
          </ul>
        </div><!-- /.row -->
        <nav class="blog-pagination">
            <a class="btn btn-outline-primary" href="#">Older</a>
            <a class="btn btn-outline-secondary disabled" href="#">Newer</a>
          </nav>
      </div><!-- /.container -->
      <footer class="blog-footer">
        <p>VueJS - Nodejs by Tengo Miedo.</p>
        <p>
          <a href="#">Back to top</a>
        </p>
      </footer>
    </div>  <!-- div logged -->
    
    
    
    <b-modal id="signinModal" ref = "signinModal" title="Signin">
      <b-form id="signinForm">
        <b-form-group id="signinEmailInputGroup"
                    label="Email address:"
                    label-for="signinEmailInput">
          <b-form-input id="signipEmailInput"
                        type="email"
                        v-model="user.email"
                        required
                        placeholder="Enter email">
          </b-form-input>
        </b-form-group>
        <b-form-group id="signinPasswordInputGroup"
                    label="Password"
                    label-for="signinPasswordInput">
          <b-form-input id="signinPasswordInput"
                        type="password"
                        v-model="user.password"
                        required
                        placeholder="Enter password">
          </b-form-input>
        
           <button @click.prevent="signin" class="btn btn-lg btn-primary btn-block" data-dismiss="alert">Sign in</button>
        </b-form-group>
        
        
      </b-form>
      
    </b-modal>
    
    
    <b-modal ref="modalSignUp" id="modalSignUp" title="SignUp" @ok="handleOk" @shown="clearUserData">
     
      <form id="signupForm" hide-footer>
        <b-form-group id="signupFirstNameInputGroup"
                    label="Firstname:"
                    label-for="signupFirstNameInput">
          <b-form-input id="signupFirstNameInput"
                      type="text"
                      v-model="user.firstname"
                      required
                      placeholder="Enter firstname">
          </b-form-input>
        </b-form-group>
        <b-form-group id="signupLastNameInputGroup"
                    label="Lastname:"
                    label-for="signupLastNameInput">
          <b-form-input id="signupLastNameInput"
                      type="text"
                      v-model="user.lastname"
                      required
                      placeholder="Enter firstname">
          </b-form-input>
        </b-form-group>
        <b-form-group id="signupEmailInputGroup"
                    label="Email address:"
                    label-for="signupEmailInput"
                    description="We'll never share your email with anyone else.">
          <b-form-input id="signupEmailInput"
                        type="email"
                        v-model="user.email"
                        required
                        placeholder="Enter email">
          </b-form-input>
        </b-form-group>
        <b-form-group id="signupPasswordInputGroup"
                    label="Password"
                    label-for="signupPasswordInput">
          <b-form-input id="signupPasswordInput"
                        type="password"
                        v-model="user.password"
                        required
                        placeholder="Enter password">
          </b-form-input>
        </b-form-group>
        <button @click.prevent="handleSubmit" class="btn btn-lg btn-primary btn-block" data-dismiss="alert">Sign in</button>
      </form>
    </b-modal>
    
    <b-modal id="loginFailModal" ref="loginFailModal" title="Authenticacion Error">
      <p class="my-4">Login process failed. Please, check on your credentials.</p>
      <div slot="modal-footer" class="w-100">
        <b-btn size="sm" class="float-right" variant="primary" @click="hideLoginFailedModal">
          Close
        </b-btn>
      </div>
    </b-modal>
    
  </div>
</template>

<script>

import axios from "axios";
import config from "./config.json";
import serialize from 'form-serialize';

import Vue from 'vue'
import BootstrapVue from 'bootstrap-vue'

Vue.use(BootstrapVue);

export default {
  name: 'app',
  data () {
    return {
      logged : false,
      loading: true,
      user: {
        firstname: '',
        lastname: '',
        email: '',
        password: ''
      },
      questions: [],
      question: {
        text: '',
        user: '',
        answers : []
      }
    }
  },
  created () {
    this.loadQuestions();
    
  },
  methods: {
    signin(){
      const form = document.getElementById('signin');
      const payload = serialize(form); 
      //console.log("payload = " + payload); console.log("user =" + this.user );

      axios.post(`${config.baseURL}/users/login`, payload, {
        withCredentials: true,
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded'
        }
      })
      .then( response => {
        this.logged = true;
        this.user.firstname = response.data.user.firstname;
        this.user.lastname = response.data.user.lastname;
        window.localStorage.setItem('token', response.data.token);
      })
      .catch ( res =>{
        //$('#signinErrorModal').modal(show);
        //var signinModal = document.getElementById("signinErrorModal");
        //signinModal.modal(show);
        this.showLoginFailedModal();
      })
    },
    
    
    
    loadQuestions(){
      axios.get(`${config.baseURL}/questions`,{
        withCredentials: true
      })
      .then(response => {
        this.loading = false;
        this.questions = response.data.data;
      })
    },
    createQuestion(){
      const form = document.getElementById('createQuestionForm');
      let payload = serialize(form);
      payload+=`&token=${window.localStorage.getItem('token')}`;
      axios.post(`${config.baseURL}/questions`, payload, {
        withCredentials: true,
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded'
        }
      })
      .then( response => {
        this.loadQuestions();
      })
    },
    
    createAnswer(event){
      let form = event.currentTarget.parentElement;
      //const form = document.getElementById('createAnswerForm');
      
      let payload = serialize(form);
      //console.log("payload = " + payload);
      //payload+=`&token=${window.localStorage.getItem('token')}`;
      
      axios.post(`${config.baseURL}/answers?token=${window.localStorage.getItem('token')}`, payload, {
        withCredentials: true,
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded'
        }
      })
      .then( response => {
        this.loadQuestions();
      })
    },
    loadAnswers(){
      axios.get(`${config.baseURL}/answers`,{
        withCredentials: true
      })
      .then(response => {
        this.loading = false;
        this.answers = response.data.data;
      })
    },
    
    
    
    
    
    showLoginFailedModal () {
      this.$refs.loginFailModal.show()
    },
    hideLoginFailedModal () {
      this.$refs.loginFailModal.hide()
    },
    clearUserData () {
      this.user.firstname = '';
      this.user.lastname = "";
      this.user.email = "";
      this.user.password = "";
    },
    handleOk (evt) {
      // Prevent modal from closing
      evt.preventDefault()
      if (!this.user.firstname) {
        alert('Please enter your first name')
        return;
      }
      if (!this.user.lastname) {
        alert('Please enter your last name')
        return;
      }
      if (!this.user.email) {
        alert('Please enter your email')
        return;
      }
      if (!this.user.password) {
        alert('Please enter your password')
        return;
      }
     
      this.handleSubmit()
      
    },
    handleSubmit () {
      // Aquí se define qué hacer con la info obtenida en el signUp
      
      const form = document.getElementById('signupForm');
      //const payload = serialize(form); 
      const payload = `firstname=${this.user.firstname}&lastname=${this.user.lastname}&email=${this.user.email}&password=${this.user.password}` 
      //console.log("payload = " + payload); console.log("user =" + this.user )

      axios.post(`${config.baseURL}/users/signup`, payload, {
        withCredentials: true,
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded'
        }
      })
      .then( response => {
        //console.log(response);
        this.logged = true;
        window.localStorage.setItem('token', response.data.token);
      })
      .catch ( res =>{
        
        this.showLoginFailedModal();
      })
      
      //this.clearUserData()
      this.$refs.modalSignUp.hide()
    },
     signout(){
      this.logged = false;
      window.localStorage.removeItem('token');
      this.clearUserData();
    }
  }
}
</script>

<style>

.img-login{
  display: block;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}


.form-signin {
  max-width: 330px;
  padding: 15px;
  margin: 0 auto;
  text-align: center;
}
.form-signin .form-signin-heading,
.form-signin .checkbox {
  margin-bottom: 10px;
}
.form-signin .checkbox {
  font-weight: normal;
}
.form-signin .form-control {
  position: relative;
  height: auto;
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
  padding: 10px;
  font-size: 16px;
}
.form-signin .form-control:focus {
  z-index: 2;
}
.form-signin input[type="email"] {
  margin-bottom: -1px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.form-signin input[type="password"] {
  margin-bottom: 10px;
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}


/*
 * Globals
 */

@media (min-width: 48em) {
  html {
    font-size: 18px;
  }
}

body {
  font-family: Georgia, "Times New Roman", Times, serif;
  color: #555;
}

h1, .h1,
h2, .h2,
h3, .h3,
h4, .h4,
h5, .h5,
h6, .h6 {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-weight: normal;
  color: #333;
}


/*
 * Override Bootstrap's default container.
 */

.container {
  max-width: 60rem;
}


/*
 * Masthead for nav
 */

.blog-masthead {
  margin-bottom: 3rem;
  background-color: #C7C7BB;
  -webkit-box-shadow: inset 0 -.1rem .25rem rgba(0,0,0,.1);
          box-shadow: inset 0 -.1rem .25rem rgba(0,0,0,.1);
}

/* Nav links */
.nav-link {
  position: relative;
  padding: 1rem;
  font-weight: 500;
  color: #fff;
}

.nav-link:hover,
.nav-link:focus {
  color: black;
  background-color: transparent;
}

/* Active state gets a caret at the bottom */
.nav-link.active {
  color: #fff;
}
.nav-link.active:after {
  position: absolute;
  bottom: 0;
  left: 50%;
  width: 0;
  height: 0;
  margin-left: -.3rem;
  vertical-align: middle;
  content: "";
  border-right: .3rem solid transparent;
  border-bottom: .3rem solid;
  border-left: .3rem solid transparent;
}


/*
 * Blog name and description
 */

.blog-header {
  padding-bottom: 1.25rem;
  margin-bottom: 2rem;
  border-bottom: .05rem solid #eee;
}
.blog-title {
  margin-bottom: 0;
  font-size: 2rem;
  font-weight: normal;
}
.blog-description {
  font-size: 1.1rem;
  color: #999;
}

@media (min-width: 40em) {
  .blog-title {
    font-size: 3.5rem;
  }
}


/*
 * Main column and sidebar layout
 */

/* Sidebar modules for boxing content */
.sidebar-module {
  padding: 1rem;
  /*margin: 0 -1rem 1rem;*/
}
.sidebar-module-inset {
  padding: 1rem;
  background-color: #f5f5f5;
  border-radius: .25rem;
}
.sidebar-module-inset p:last-child,
.sidebar-module-inset ul:last-child,
.sidebar-module-inset ol:last-child {
  margin-bottom: 0;
}


/* Pagination */
.blog-pagination {
  margin-bottom: 4rem;
}
.blog-pagination > .btn {
  border-radius: 2rem;
}


/*
 * Blog posts
 */

.blog-post {
  margin-bottom: 4rem;
}
.blog-post-title {
  margin-bottom: .25rem;
  font-size: 2.5rem;
}
.blog-post-meta {
  margin-bottom: 1.25rem;
  color: #999;
}


/*
 * Footer
 */

.blog-footer {
  padding: 2.5rem 0;
  color: #999;
  text-align: center;
  background-color: #f9f9f9;
  border-top: .05rem solid #e5e5e5;
}
.blog-footer p:last-child {
  margin-bottom: 0;
}

.answers-div{
  margin-left: 35px;
}

.btn-div{
  margin-top: 15px;
  display: block;
  text-align: right;
}

.btn-color{
  background-color: #C7C7BB !important;
  font-weight: bold;
}

.list-group-item{
  border: 0px solid rgba(0,0,0,.125) !important;
  border-left: 1px solid rgba(0,0,0,.125) !important;
  border-bottom: 1px solid rgba(0,0,0,.125) !important;
}

.answers-li{
  margin-bottom: 15px;
}

.questions-border{
  padding-right: 45px;
  border-right: 3px solid rgba(199,199,187,5) !important;
  
}

.ask-question{
  background-color: rgba(245,245,245,1);
  padding-top: 1rem;
  padding-bottom: 1.3rem;
  margin-left:0;
  margin-right:0;
  margin-bottom: 30px;
  border-bottom: 2px solid rgba(199,199,187,1) !important;
  border-bottom-left-radius: 80px;
  border-bottom-right-radius: 80px;
}

.container-question {
  background-color: rgba(233,126,59,.9);
  border-radius: 15px;
  padding: 15px;
  
}

.blog-masthead {
 margin-bottom: 0 !important;
}

.ask-something{
  color: white;
}

</style>
