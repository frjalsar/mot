<template>
  <div>    
    <div v-for="comp in competition" :key="comp" class="md-layout md-gutter">

      <div class="md-layout-item">
        <md-field>
          <label>Grein</label>          
          <md-select v-model="comp.event" name="events" id="events">
            <md-optgroup v-for="cat in eventCategories" :key="cat" :label="cat">
              <md-option v-for="evt in eventsByCategories(cat)" :key="evt.id" :value="evt.id">{{ evt.name }}</md-option>              
            </md-optgroup>
          </md-select>
        
        </md-field>
      </div>

      <div class="md-layout-item">
        <md-field>
          <label>Kyn</label>
          <md-select v-model="comp.gender" name="gender" id="gender">
            <md-option v-for="gender in genders" :key="gender.id" :value="gender.id">{{ gender.name }}</md-option>
          </md-select>
        
        </md-field>
      </div>

      <div class="md-layout-item">
        <md-field>
          <label>Lýsing</label>
          <md-input v-model="comp.name"></md-input>        
        </md-field>
      </div>

      <div class="md-layout-item">
        <md-field>
          <label>Tímasetning</label>
          <md-input v-model="comp.time"></md-input>
          <md-icon>access_time</md-icon>
        </md-field>
      </div>

       <div class="md-layout-item">
        <md-field>
          <label>Aldur frá</label>
          <md-input v-model="comp.minAge"></md-input>
        </md-field>
      </div>

      <div class="md-layout-item">
        <md-field>
          <label>Aldur til</label>
          <md-input v-model="comp.maxAge"></md-input>
        </md-field>
      </div>

      <div class="md-layout-item">
        <md-field>
          <label>Forveri</label>
          <md-select v-model="comp.prereq" name="prerequisite" id="prerequisite">
            <md-option v-for="prereq in getPrerequisites(comp)" :key="prereq" :value="prereq.event">{{ prereq.name }}</md-option>
          </md-select>
        </md-field>
      </div>
    </div>
    
    <div class="md-layout md-gutter">

      <div class="md-layout-item">
        <md-button class="md-raised" @click="addEmptyLine">Bæta við</md-button>
      </div>

    </div>    
  </div>
</template>

<script>
import uniqBy from 'lodash.uniqby'
import groupBy from 'lodash.groupby'
export default {
  name: 'CreateTimesheet',
  props: [
    'events'
  ],
  data() {
    return {
      selected: {},
      genders: [
        {
          id: 1,
          name: 'Karlar'
        },
        {
          id: 2,
          name: 'Konur'
        }
      ],
      competition: []
    }
  },
  computed: {    
    eventCategories() {
      return uniqBy(this.events, 'category').map(events => events.category)
    }
  },
  mounted() {
    this.addEmptyLine()
  },
  watch: {
    events() {
      /*
      this.events.forEach(event => {
        console.log('já')
        this.competition.push({
          event: event.id,
          gender: 1,
          time: '',
          minAge: '',
          maxAge: ''
        })
      })  
      */ 
    }    
  },
  methods: {
    getPrerequisites(comp) {
      return this.competition.filter(item => {
        console.log(item)
        const isSameEvent = item.event === comp.event
        const isSameGender = item.gender === comp.gender
        const isDifferentTime = item.time !== comp.time
        return isSameEvent && isSameGender && isDifferentTime
      })
    },
    eventsByCategories(cat) {
      if (!cat) {
        return []
      }
      return groupBy(this.events, 'category')[cat]
    },
    addEmptyLine() {
      this.competition.push({
        event: '',
        gender: '',
        time: '',
        minAge: '',
        maxAge: ''
      })
    }  
  }
}
</script>