<template>
<div>

  <div class="md-layout">    
    <div class="md-layout-item">
      <md-list>
        <span class="md-title">Spretthlaup</span>
        <md-list-item v-for="event in eventList.filter(obj => obj.category === 'Spretthlaup')" :key="event.id">
          <md-checkbox v-model="events" @change="save" :value="event">{{ event.name }}</md-checkbox>
        </md-list-item>        
      </md-list>
    </div>
  
    <div class="md-layout-item"> 
      <md-list>
        <span class="md-title">Millivega- og langhlaup</span>
        <md-list-item v-for="event in eventList.filter(obj => obj.category === 'Millivega- og langhlaup')" :key="event.id">
          <md-checkbox v-model="events" @change="save" :value="event">{{ event.name }}</md-checkbox>
        </md-list-item>        
      </md-list>       
    </div>

    <div class="md-layout-item"> 
      <md-list>
        <span class="md-title">Stökk</span>
        <md-list-item v-for="event in eventList.filter(obj => obj.category === 'Stökk')" :key="event.id">
          <md-checkbox v-model="events" @change="save" :value="event">{{ event.name }}</md-checkbox>
        </md-list-item>        
      </md-list>       
    </div>

    <div class="md-layout-item"> 
      <md-list>
        <span class="md-title">Köst</span>
        <md-list-item v-for="event in eventList.filter(obj => obj.category === 'Köst')" :key="event.id">
          <md-checkbox v-model="events" @change="save" :value="event">{{ event.name }}</md-checkbox>
        </md-list-item>        
      </md-list>       
    </div>

    <div class="md-layout-item"> 
      <md-list>
        <span class="md-title">Þrautir</span>
        <md-list-item v-for="event in eventList.filter(obj => obj.category === 'Þrautir')" :key="event.id">
          <md-checkbox v-model="events" @change="save" :value="event">{{ event.name }}</md-checkbox>
        </md-list-item>        
      </md-list>       
    </div>

</div>
</template>

<script>

export default {
  name: 'AddEvents',  
  data () {
    return {
      events: [],
      eventList: [
        {
          id: 1,
          name: '30 m',
          category: 'Spretthlaup'
        },{
          id: 2,
          name: '60 m',
          category: 'Spretthlaup'
        },{
          id: 3,
          name: '100 m',
          category: 'Spretthlaup'
        },{
          id: 4,
          name: '200 m',
          category: 'Spretthlaup'
        },{
          id: 5,
          name: '400 m',
          category: 'Spretthlaup'
        },{
          id: 6,
          name: '800 m',
          category: 'Millivega- og langhlaup'
        },{
          id: 7,
          name: '1.500 m',
          category: 'Millivega- og langhlaup'
        },{
          id: 8,
          name: 'Míla',
          category: 'Millivega- og langhlaup'
        },{
          id: 9,
          name: '3.000 m',
          category: 'Millivega- og langhlaup'
        },{
          id: 10,
          name: '5.000 m',
          category: ''
        },{
          id: 11,
          name: '10.000 m',
          category: 'Millivega- og langhlaup'
        },{
          id: 12,
          name: 'Kúluvarp',
          category: 'Köst'
        },{
          id: 13,
          name: 'Sleggjakast',
          category: 'Köst'
        },{
          id: 14,
          name: 'Kringlukast',
          category: 'Köst'
        },{
          id: 15,
          name: 'Langstökk',
          category: 'Stökk'
        },{
          id: 16,
          name: 'Þrístökk',
          category: 'Stökk'
        },{
          id: 17,
          name: 'Hástökk',
          category: 'Stökk'
        },{
          id: 18,
          name: 'Stangarstökk',
          category: 'Stökk'
        },{
          id: 19,
          name: 'Sjöþraut',
          category: 'Þrautir'
        },{
          id: 20,
          name: 'Tugþraut',
          category: 'Þrautir'
        }
      ]
    }
  },
  methods: {
    save() {
      this.$emit('input', this.events)
    }
  }
}
</script>