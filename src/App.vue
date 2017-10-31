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
                    <i class="paypal icon"></i>
                        Manage
                </a>
                <a class="item" @click="panel6.v=true" href='#drawer6'>
                    <i class="sidebar icon"></i>
                        About
                </a>
            </div>
        </div>

    </div>


    <div class="one column row">

            <div>
                  <!-- Left Floating Card -->
                  <div class="ui card left floated three wide column" style="margin-top: 50px; margin-left: 90px;">
                      
                      <div class="content">
                          <div class="header">Project Timeline</div>
                      </div>
                      
                      <div class="content">
                          
                          <h4 class="ui sub header">Activity</h4>
                          
                          <div class="ui small feed">
                              
                              <div class="event">
                                <div class="content">
                                    <div class="summary">
                                      <a>Elliot Fu</a> added <a>Jenny Hess</a> to the project
                                    </div>
                                </div>
                            </div>
                            
                            <div class="event">
                              <div class="content">
                                <div class="summary">
                                    <a>Stevie Feliciano</a> was added as an <a>Administrator</a>
                                </div>
                              </div>
                            </div>
                          
                            <div class="event">
                              <div class="content">
                                  <div class="summary">
                                      <a>Helen Troy</a> added two pictures
                                  </div>
                              </div>
                            </div>
                          </div>
                      </div>
                  
                  <div class="extra content">
                    <button class="ui button">Join Project</button>
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
                    <i class="marker icon"></i>
                        Staff
                </a>
                <a class="item" @click="panel3.v=true" href='#drawer3'>
                    <i class="paypal icon"></i>
                        Manage
                </a>
                <a class="item" @click="panel6.v=true" href='#drawer6'>
                    <i class="sidebar icon"></i>
                        About
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

         <div>
           <input type="checkbox" id="chb" v-model="panel7.v">
           <label for="chb">Drawer 7</label>
         </div>

         {{lorem}}

         <vue-slideout-panel v-model="panel7.v"
              :widths="['40%']"
              @close="panel7.v=false">
              {{lorem}}
         </vue-slideout-panel>

      <div slot="extra">{{lorem}}</div>

    </vue-slideout-panel>



  </div>

  </div>
</template>

<script>
  import VueSlideoutPanel from 'vue-slideout-panel'
  import sweetalert from 'sweetalert';
  import EmployeeList from './components/EmployeeList';
  import CreateEmployee from './components/CreateEmployee';



  let lorem = "Lorem ipsum dolor sit amet, consectetur adipiscing elit,\
sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.\
Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.\
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.\
Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.";

  let staff = [{
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
      }];

export default {
  name: 'app',

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
      staff: staff,
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

      panel7: {v:false}

    }
  },

  components: {

    VueSlideoutPanel,
    EmployeeList,
    CreateEmployee,
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
