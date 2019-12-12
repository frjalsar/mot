<template>
  <div class="page-container">
    <md-app>    
      <md-app-toolbar class="md-primary">
        <h3 class="md-title">Mótaforrit FRÍ</h3>      
      </md-app-toolbar>

      <md-app-content>
        <md-tabs>
          <md-tab id="step-meet" md-label="Mót">        
            <CreateMeet @input="updateMeet"/>          
          </md-tab>
          <md-tab id="step-" md-label="Greinar">
            <AddEvents @input="updateEvents"/>          
          </md-tab>
          <md-tab id="step-posts" md-label="Tímaseðill">
            <CreateTimesheet :events="events" />
          </md-tab>      
        </md-tabs>
      </md-app-content>
    </md-app>    
  </div>
</template>

<script>
import CreateMeet from './meet/create'
import AddEvents from './events/add'
import CreateTimesheet from './timesheet/create'
export default {
  name: 'App',
  components: {
    CreateMeet,
    AddEvents,
    CreateTimesheet
  },
  data () {
    return {
      meet: {},
      events: []
    }
  },
  methods: {
    updateMeet(meet) {
      this.meet = meet
    },
     updateEvents(events) {      
      this.events = events
    }
  }
}
</script>