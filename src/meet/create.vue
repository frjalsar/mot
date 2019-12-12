<template>
<div>

  <div class="md-layout md-gutter">
    <div class="md-layout-item">
      <md-field>
        <label>Heiti</label>
        <md-input v-model="name" @blur="save"></md-input>
      </md-field>
    </div>  

    <div class="md-layout-item">
      <md-datepicker v-model="startDate" @input="save">
        <label>Byrjar</label>
      </md-datepicker>
    </div>

    <div class="md-layout-item">
      <md-datepicker v-model="endDate" @input="save">
        <label>Endar</label>
      </md-datepicker>
    </div>
  </div>

</div>
</template>

<script>

export default {
  name: 'CreateMeet',
  data () {
    return {
      name: '',
      startDate: '',
      endDate: ''
    }
  },
  methods: {
    save() {
      this.$emit('input', {
        name: this.name,
        startDate: this.startDate,
        endDate: this.endDate
      })
    }
  }
}
</script>