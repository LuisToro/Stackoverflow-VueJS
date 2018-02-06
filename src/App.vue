<template>
  <div id="app">
   <div v-if="!logged" class="container">
     <!-- Login -->
      <img src="./assets/logoStack.png" alt="Logo Stackoverflow" class="img-login" height="100" width="100">
      <form id="signin" class="form-signin">
        <h2 class="form-signin-heading">Stackoverflow</h2>
        <h4 class="form-signin-heading" style="padding-bottom: 15px;">Please sign in</h4>
        <label for="inputEmail" class="sr-only">Email address</label>
        <input type="email" id="inputEmail" class="form-control" placeholder="Email address" name="email" v-model="user.email" required autofocus>
        <label for="inputPassword" class="sr-only">Password</label>
        <input type="password" id="inputPassword" class="form-control" placeholder="Password" name="password" v-model="user.password" required>
        <button @click.prevent="signin" class="btn btn-lg btn-primary btn-block" data-dismiss="alert">Sign in</button>
        <button class="btn btn-lg btn-success btn-block" data-toggle="modal" data-target="#exampleModal">Sign up</button>
        <b-btn v-b-modal.myModal class="btn btn-lg btn-block" variant="success">Show Modal</b-btn>
      </form>
      <!-- Fin Login -->
    </div> <!-- /container -->
    
    <!-- Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <form id="signUp">
            <div class="modal-header">
              <h5 class="modal-title" id="exampleModalLabel">SignUp</h5>
              <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
              </button>
            </div>
            <div class="modal-body">
              <label for="inputFirstname">Firstname</label>
              <input type="text" id="inputFirstname" class="form-control" placeholder="First Name" name="firstname" v-model="user.firstname" required >
              <label for="inputLastname">Lastname</label>
              <input type="text" id="inputLastname" class="form-control" placeholder="Last Name" name="lastname" v-model="user.lastname" required >
              <label for="inputEmail">Email address</label>
              <input type="email" id="inputNewEmail" class="form-control" placeholder="Email address" name="email" v-model="user.email" required >
            </div>
            <div class="modal-footer">
              <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
              <button @click.prevent="signup" type="button" class="btn btn-primary">SignUp</button>
            </div>
          </form>
        </div>
      </div>
    </div>
    <!-- fin modal -->
    
    <!-- Inicio   -->
    <div v-if="logged"> 
      <div class="blog-masthead">
      <div class="container">
        <nav class="nav blog-nav">
          <img src="./assets/logoNavbar.png" alt="Logo Stackoverflow" height="50" width="auto">
          <a class="nav-link active" href="#">Question</a>
        </nav>
      </div>
    </div>

    <div class="blog-header">
      <div class="container">
        <h1 class="blog-title">The Bootstrap Blog</h1>
        <p class="lead blog-description">An example blog template built with Bootstrap.</p>
      </div>
    </div>

    <div class="container">

      <div class="row">

        <div class="col-sm-8 blog-main">

          <div class="blog-post">
            <h2 class="blog-post-title">Sample blog post</h2>
            <p class="blog-post-meta">January 1, 2014 by <a href="#">Mark</a></p>

            <p>This blog post shows a few different types of content that's supported and styled with Bootstrap. Basic typography, images, and code are all supported.</p>
            <hr>
            <p>Cum sociis natoque penatibus et magnis <a href="#">dis parturient montes</a>, nascetur ridiculus mus. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Sed posuere consectetur est at lobortis. Cras mattis consectetur purus sit amet fermentum.</p>
            <blockquote>
              <p>Curabitur blandit tempus porttitor. <strong>Nullam quis risus eget urna mollis</strong> ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.</p>
            </blockquote>
            <p>Etiam porta <em>sem malesuada magna</em> mollis euismod. Cras mattis consectetur purus sit amet fermentum. Aenean lacinia bibendum nulla sed consectetur.</p>
            <h2>Heading</h2>
            <p>Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Morbi leo risus, porta ac consectetur ac, vestibulum at eros.</p>
            <h3>Sub-heading</h3>
            <p>Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.</p>
            <pre><code>Example code block</code></pre>
            <p>Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa.</p>
            <h3>Sub-heading</h3>
            <p>Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
            <ul>
              <li>Praesent commodo cursus magna, vel scelerisque nisl consectetur et.</li>
              <li>Donec id elit non mi porta gravida at eget metus.</li>
              <li>Nulla vitae elit libero, a pharetra augue.</li>
            </ul>
            <p>Donec ullamcorper nulla non metus auctor fringilla. Nulla vitae elit libero, a pharetra augue.</p>
            <ol>
              <li>Vestibulum id ligula porta felis euismod semper.</li>
              <li>Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.</li>
              <li>Maecenas sed diam eget risus varius blandit sit amet non magna.</li>
            </ol>
            <p>Cras mattis consectetur purus sit amet fermentum. Sed posuere consectetur est at lobortis.</p>
          </div><!-- /.blog-post -->

          <div class="blog-post">
            <h2 class="blog-post-title">Another blog post</h2>
            <p class="blog-post-meta">December 23, 2013 by <a href="#">Jacob</a></p>

            <p>Cum sociis natoque penatibus et magnis <a href="#">dis parturient montes</a>, nascetur ridiculus mus. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Sed posuere consectetur est at lobortis. Cras mattis consectetur purus sit amet fermentum.</p>
            <blockquote>
              <p>Curabitur blandit tempus porttitor. <strong>Nullam quis risus eget urna mollis</strong> ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.</p>
            </blockquote>
            <p>Etiam porta <em>sem malesuada magna</em> mollis euismod. Cras mattis consectetur purus sit amet fermentum. Aenean lacinia bibendum nulla sed consectetur.</p>
            <p>Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Morbi leo risus, porta ac consectetur ac, vestibulum at eros.</p>
          </div><!-- /.blog-post -->

          <div class="blog-post">
            <h2 class="blog-post-title">New feature</h2>
            <p class="blog-post-meta">December 14, 2013 by <a href="#">Chris</a></p>

            <p>Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
            <ul>
              <li>Praesent commodo cursus magna, vel scelerisque nisl consectetur et.</li>
              <li>Donec id elit non mi porta gravida at eget metus.</li>
              <li>Nulla vitae elit libero, a pharetra augue.</li>
            </ul>
            <p>Etiam porta <em>sem malesuada magna</em> mollis euismod. Cras mattis consectetur purus sit amet fermentum. Aenean lacinia bibendum nulla sed consectetur.</p>
            <p>Donec ullamcorper nulla non metus auctor fringilla. Nulla vitae elit libero, a pharetra augue.</p>
          </div><!-- /.blog-post -->

          <nav class="blog-pagination">
            <a class="btn btn-outline-primary" href="#">Older</a>
            <a class="btn btn-outline-secondary disabled" href="#">Newer</a>
          </nav>

        </div><!-- /.blog-main -->

        <div class="col-sm-3 offset-sm-1 blog-sidebar">
          <div class="sidebar-module sidebar-module-inset">
            <h4>About</h4>
            <p>Etiam porta <em>sem malesuada magna</em> mollis euismod. Cras mattis consectetur purus sit amet fermentum. Aenean lacinia bibendum nulla sed consectetur.</p>
          </div>
          <div class="sidebar-module">
            <h4>Archives</h4>
            <ol class="list-unstyled">
              <li><a href="#">March 2014</a></li>
              <li><a href="#">February 2014</a></li>
              <li><a href="#">January 2014</a></li>
              <li><a href="#">December 2013</a></li>
              <li><a href="#">November 2013</a></li>
              <li><a href="#">October 2013</a></li>
              <li><a href="#">September 2013</a></li>
              <li><a href="#">August 2013</a></li>
              <li><a href="#">July 2013</a></li>
              <li><a href="#">June 2013</a></li>
              <li><a href="#">May 2013</a></li>
              <li><a href="#">April 2013</a></li>
            </ol>
          </div>
          <div class="sidebar-module">
            <h4>Elsewhere</h4>
            <ol class="list-unstyled">
              <li><a href="#">GitHub</a></li>
              <li><a href="#">Twitter</a></li>
              <li><a href="#">Facebook</a></li>
            </ol>
          </div>
        </div><!-- /.blog-sidebar -->

      </div><!-- /.row -->

    </div><!-- /.container -->

    <footer class="blog-footer">
      <p>Blog template built for <a href="https://getbootstrap.com">Bootstrap</a> by <a href="https://twitter.com/mdo">@mdo</a>.</p>
      <p>
        <a href="#">Back to top</a>
      </p>
    </footer>
    </div>
    
    <b-modal id="myModal" title="SignUp" @ok="handleOk" @shown="clearName">
     
      <form @submit.stop.prevent="handleSubmit">
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
      </form>
    </b-modal>
    
    <b-modal id="loginFailModal" ref="loginFailModal" title="Authenticacion Error">
      <p class="my-4">Login process failed. Please, check on your credentials.</p>
      <div slot="modal-footer" class="w-100">
        <b-btn size="sm" class="float-right" variant="primary" @click="hideModal">
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
      msg: 'Welcome to Your Vue.js App',
      logged : false,
      user: {
        firstname: '',
        lastname: '',
        email: '',
        password: '',
      }
    }
  },
  created () {
    //$('.alert').alert();
    
  },
  methods: {
    signin(){
      const form = document.getElementById('signin');
      const payload = serialize(form);

      axios.post(`${config.baseURL}/users/login`, payload, {
        withCredentials: true,
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded'
        }
      })
      .then( response => {
        console.log(response);
        this.logged = true;
        window.localStorage.setItem('token', response.data.token);
      })
      .catch ( res =>{
        console.log("response = "+res);
        //$('#signinErrorModal').modal(show);
        //var signinModal = document.getElementById("signinErrorModal");
        //signinModal.modal(show);
        this.showModal();
      })
    },
    showModal () {
      this.$refs.loginFailModal.show()
    },
    hideModal () {
      this.$refs.loginFailModal.hide()
    },
    clearName () {
      this.user.firstname = ''
    },
    handleOk (evt) {
      // Prevent modal from closing
      evt.preventDefault()
      if (!this.user.firstname) {
        alert('Please enter your name')
      } else {
        this.handleSubmit()
      }
    },
    handleSubmit () {
      // Aquí se define qué hacer con la info obtenida en el signUp
      //this.user.firstname = this.firstname;
      this.clearName()
      this.$refs.myModal.hide()
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
  color: #cdddeb;
}
.nav-link:hover,
.nav-link:focus {
  color: #fff;
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
</style>
