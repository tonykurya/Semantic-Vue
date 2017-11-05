<template>
  <div class="ui grid">
    
    <div class="two column row" style="margin-top: 10px;">
        

        <!-- Logo -->
        <div class="left floated column" style="margin-left: 15px;">
              <img src="./assets/logo.png" alt="logo" height="50px" width="50px">
        </div>


        <!-- Floating Navbar -->
        <div class="right floated" style="margin-right: 30px">
            <div class="ui compact menu">

                <a class="item" @click="panel2.v=true" href='#drawer2'>
                    <i class="users icon"></i>
                        Staff
                </a>
                <a class="item" @click="panel3.v=true" href='#drawer3'>
                    <i class="street view icon"></i>
                        Manage
                </a>
                <a class="item" @click="panel6.v=true" href='#drawer6'>
                    <i class="map signs icon"></i>
                       About Us 
                </a>
            </div>
        </div>

    </div>


    <div class="one column row">

            <div>
                  <!-- Left Floating Card -->
                  <div class="ui card left floated three wide column" style="margin-top: 50px; margin-left: 90px; background-color: #CCD9CE">
                      
                      <div class="content">
                          <div class="header" style="color: #008080" >Temper</div>
                      </div>
                      
                      <div class="content">
                                                    
                          <div class="ui small feed">
                              
                              <div class="event">
                                <div class="content">
                                    <div class="summary">
                                        Join our webinar on <a>Nov. 17th</a> to learn how new complex labor laws and agreements impact hourly workers.<br> Register: <a>hhttps://temper/webinar</a>


                                    </div>
                                </div>
                            </div>
                            
                          
                            <div class="event">
                              <div class="content">
                                  <div class="summary">
                                      <img src="https://pbs.twimg.com/media/DNv-RFLVAAEARhd.png" alt="webinar">
                                  </div>
                              </div>
                            </div>
                          </div>
                      </div>
                  
                  <div class="extra content">
                    <button class="ui teal button">Join Webinar</button>
                  </div>

                  </div>

              </div>  


              <!-- Floating Names -->
            <div class="ui horizontal list column" style="paddingTop: 10px">
                <div class="item">
                  <img class="ui mini circular image" src="/images/avatar2/small/molly.png">
                  <div class="content">
                    <div class="ui sub header">Molly</div>
                    Coordinator
                  </div>
                </div>
                <div class="item">
                  <img class="ui mini circular image" src="/images/avatar2/small/elyse.png">
                  <div class="content">
                    <div class="ui sub header">Elyse</div>
                    Developer
                  </div>
                </div>
                <div class="item">
                  <img src="/images/avatar2/small/eve.png" class="ui mini circular image">
                  <div class="content">
                    <div class="ui sub header">Eve</div>
                    Project Manager
                  </div>
                </div>
            </div>





    <vue-slideout-panel v-model="panel1.v" @close="panel1.v=false">
        <div class='ui two column centered grid'>
          <div class='column'>
            <employee-list v-bind:staff="staff"></employee-list>
            <create-employee v-on:create-employee="createEmployee"></create-employee>
          </div>
        </div>        
    </vue-slideout-panel>





    <vue-slideout-panel v-model="panel2.v" :count=2 @close="panel2.v=false" :classes="['']" :styles="panel2.styles"

>
      <nav-bar>
        <div>
            <div class="ui compact menu right floated">

                <a class="item" @click="panel2.v=true" href='#drawer2'>
                    <i class="users icon"></i>
                        Staff
                </a>
                <a class="item" @click="panel3.v=true" href='#drawer3'>
                    <i class="street view icon"></i>
                        Manage
                </a>
                <a class="item" @click="panel6.v=true" href='#drawer6'>
                    <i class="map signs icon"></i>
                       About Us 
                </a>
            </div>
        </div>
      </nav-bar>
        

        <div class="ui divider"></div>
        <div class="ui divider"></div>


        <div class="ui middle aligned divided list">
            <div class="item" v-bind:staff="staff" v-for="entry in staff">
              <div class="right floated content">
                <div class="ui teal button">{{ entry.role }}</div>
              </div>
              <img class="ui avatar image" src="https://secure.gravatar.com/avatar/0e678440e8e843eec12ec8aaa0e430e6">
              <div class="content">
                <h3>{{ entry.name }}</h3>
              </div>
            </div>
        </div>

  
  
        <div slot="extra">
          <div class='ui two column centered grid'>
            <div class='column'>
              <employee-list v-bind:staff="staff"></employee-list>
              <create-employee v-on:create-employee="createEmployee"></create-employee>
            </div>
          </div> 
        </div>

    </vue-slideout-panel>





    <vue-slideout-panel v-model="panel3.v"
         closeHtml='<i class="ti-close" aria-hidden="true"></i>'
         :widths="['30%']"
         :styles="panel3.styles"
         @close="panel3.v=false">
         
          <div class='ui one column centered grid'>
            <div class='column'>
              <employee-list v-bind:staff="staff"></employee-list>
              <create-employee v-on:create-employee="createEmployee"></create-employee>
            </div>
          </div> 
    </vue-slideout-panel>





    <vue-slideout-panel v-model="panel4.v"
         :count=2
         :showExtra=true
         :widths="['col-8', '60%']"
         :styles="[{padding:0},{padding:'1rem 1rem 4rem'},{same:true}]"
         :classes="['','bg-success','same']"
         closeHtml="<button class='btn btn-success'> Success</button>"
         closeAllHtml='<button class="btn btn-success"><i class="ti-share-alt" aria-hidden="true"></i></button>'
         extraHtml="<button class='btn btn-success'><i class='ti-control-forward' aria-hidden='true'></i></button>"
         @close="panel4.v=false">
         {{lorem}}
         <div slot="extra">{{lorem}}</div>
    </vue-slideout-panel>





    <vue-slideout-panel v-model="panel5.v"
         :count=2
         :widths="['col-8', '40%']"
         :styles="[{padding:0},{padding:'1rem 1rem 4rem'},{same:true}]"
         :classes="['','bg-warning','bg-warning']"
         closeHtml="<button class='btn btn-warning'>Close</button>"
         closeAllHtml="<button class='btn btn-warning'><i class='ti-share-alt' aria-hidden='true'></i></button>"
         extraHtml="<button class='btn btn-warning'><i class='ti-control-forward' aria-hidden='true'></i></button>"
         @close="panel5.v=false">
         {{lorem}}
         <div slot="extra">{{lorem}}</div>
    </vue-slideout-panel>





    <vue-slideout-panel v-model="panel6.v"
         :count=2
         :widths="['70%', '70%']"
         @close="panel6.v=false">

<!--          <div>
           <input type="checkbox" id="chb" v-model="panel7.v">
           <label for="chb">Drawer 7</label>
         </div> -->

        <div class="ui toggle checkbox">
          <input type="checkbox" name="public"  v-model="panel7.v" :styles="panel7.styles">
          <label>Subscribe</label>
        </div>
     

        <div class="ui vertical stripe segment">
          <div class="ui middle aligned stackable grid container">
            <div class="row">
              <div class="eight wide column">
                <h3 class="ui header">Smarter, Simpler Employee Scheduling</h3>
                <p>Scheduling and workforce management software to create the best schedules, simplify tracking and reporting and handle the unexpected.</p>
                <h3 class="ui header">We can give your company superpowers</h3>
                <p>Yes that's right, you thought it was the stuff of dreams, but even staff scheduling can be bioengineered.</p>
              </div>
              <div class="six wide right floated column">
                <img src="http://www.alkhwarizm.com/alkh-website/images/HR/Employee.png" class="ui large bordered rounded image">
              </div>
            </div>
          </div>
        </div>


        <div class="ui vertical stripe quote segment">
          <div class="ui equal width stackable internally celled grid">
            <div class="center aligned row">
              <div class="column">
                <h3>"What a Company"</h3>
                <p>That is what they all say about us</p>
              </div>
              <div class="column">
                <h3>"Temper gives us clear visibility of all our staff's schedules through one easy website."</h3>
                <p>
                  <img src="https://images.unsplash.com/photo-1442120108414-42e7ea50d0b5?fit=crop&fm=jpg&h=725&ixjsv=2.0.0&ixlib=rb-0.3.5&q=80&w=1225" class="ui avatar image"> <b>Chan</b> Chief Executive Officer NetFX
                </p>
              </div>
            </div>
          </div>
        </div>

        <div class="ui vertical stripe segment">
          <div class="ui text container">
            <h3 class="ui header">Manage your employees from anywhere.</h3>
            <p>Working from home or on the go? Temper is with you wherever you need it. There's nothing to install and nothing to download. Everything you need to manage your employees is right here in your web browser.</p>
            <h4 class="ui horizontal header divider">
              <a href="#">Billing</a>
            </h4>
            <h3 class="ui header">Free scheduling for small teams, forever.</h3>
            <p>Managing a small team of 5 or less? You get to schedule your employees for free, forever! More than 5 employees? You'll never pay more than $35 per month as Temper is priced per team, not per employee. FREE forever for 5 STAFF OR LESS $35 per month for BUSINESSES $26.25 per month for VOLUNTEERS</p>
            <a href="/" class="ui large teal basic button">Explore Our Live Demo</a>
          </div>
        </div>



         <vue-slideout-panel v-model="panel7.v"
              :widths="['40%']"
              @close="panel7.v=false">
              
                <div class="ui text container">
                  
                    <h2>We promise not to Spam you.</h2>
                    
                    <div class="ui huge primary button">Subscribe 
                      <i class="right arrow icon"></i>
                    </div>
                </div>

         </vue-slideout-panel>

              <div slot="extra">
                <div class="ui container">
                  <div class="ui card" style="background-color: #56c4ac">
                    <div class="content">
                      <div class="header">Basic</div>
                      <div class="meta">Automation tools for basic scheduling needs</div>
                      <div class="description">
                        <p><h1>$0</h1></p>
                        <p><h5>PER USER</h5></p>
                      </div>
                    </div>
                    <div class="extra content">
                      <button class="ui black button">Request Demo</button>
                    </div>
                  </div>


                  <div class="ui card" style="background-color: #243457">
                    <div class="content">
                      <div class="header">Professional</div>
                      <div class="meta">Perfect for most - all the key tools to optimize scheduling</div>
                      <div class="description">
                        <p><h1>$26.25</h1></p>
                        <p><h5>PER USER</h5></p>
                      </div>
                    </div>
                    <div class="extra content">
                      <button class="ui black button">Request Demo</button>
                    </div>
                  </div>


                  <div class="ui card" style="background-color: #f05624">
                    <div class="content">
                      <div class="header">Enterprise</div>
                      <div class="meta">Robust workforce management for larger organizations</div>
                      <div class="description">
                        <p><h1>$35</h1></p>
                        <p><h5>PER USER</h5></p>
                      </div>
                    </div>
                    <div class="extra content">
                      <button class="ui black button">Request Demo</button>
                    </div>
                  </div>




          </div>

        </div>

    </vue-slideout-panel>



  </div>

  </div>
</template>

<script>
  import VueSlideoutPanel from 'vue-slideout-panel'
  import sweetalert from 'sweetalert';
  import EmployeeList from './components/EmployeeList';
  import CreateEmployee from './components/CreateEmployee';


  let lorem = "Smarter, Simpler Employee Scheduling\
Purpose Built for Shift Workforces\
Managing a staff can be a headache even without staffing concerns. \
Don't let unmanned shifts and over-budgeted tasks give you grief.\
Scheduling is a thankless job. It takes time and thought to put the \
right workers into the right shifts in the right locations so that employees \
are happy and labor costs don't overrun sales. Your reward for getting it right? \
Doing it all over again the next pay period\
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.\
Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.";

  // let staff = [{
  //       name: 'Luka Modric',
  //       role: 'Security',
  //       linked: false,
  //     }, {
  //       name: 'Cornellius Van-Dar-Bilt',
  //       role: 'Manager',
  //       linked: true,
  //     }, {
  //       name: 'Patrick Kluivert',
  //       role: 'Engineer',
  //       linked: false,
  //     }, {
  //       name: 'Milan Baros',
  //       role: 'Chef',
  //       linked: false,
  //     }];

export default {
  name: 'app',

  components: {

    VueSlideoutPanel,
    EmployeeList,
    CreateEmployee,
  },

  mounted() {
    $('a[href*=\\#]').on('click', function(event){
        event.preventDefault();
        $('html,body').animate({scrollTop:$(this).offset().top}, 400);
    });
  },

  data() {
    return {
      value: 1,

      lorem: lorem,

      staff: [{
        name: 'Luka Modric',
        role: 'Security',
        linked: false,
      }, {
        name: 'Cornellius Van-Dar-Bilt',
        role: 'Manager',
        linked: true,
      }, {
        name: 'Patrick Kluivert',
        role: 'Engineer',
        linked: false,
      }, {
        name: 'Milan Baros',
        role: 'Chef',
        linked: false,
      }],

      panel1: {
        v:false
      },

      panel2: {
        v:false,
        styles: [
          {},
          {backgroundColor: '#000000', opacity: '0.9', color: '#fff'
}
        ]
      },

      panel3: {
        v:false,
        styles: [
          {},
          {
            backgroundColor: '#fff',
            opacity: 0.9,
            paddingTop: '2rem',
            paddingBottom: '1rem'
          },
          {},
          {
            color: '#555',
            textDecoration: 'none',
            top: '8px',
            right: '1rem'
          }
        ]

      },

      panel4: {
        v:false
      },

      panel5: {
        v:false
      },

      panel6: {
        v:false
      },

      panel7: {v:false},
      styles: [
        {},
        {backgroundColor: '#1b1c1d'}
      ]
    }
  },

  methods: {
    createEmployee(newEmployee) {
      this.staff.push(newEmployee);
      sweetalert('Success!', 'A new employee was created!', 'success');
    },
  }
}
</script>

<style>
  @font-face {
   font-family: 'Quicksand', sans-serif;
  }
</style>

<style scoped>

</style>
