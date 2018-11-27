<template>
  <div>
    <label for='name'>Hospital Name</label>
    <input
      id='name'
      ref='name'
      v-model='name'
      type='text'
      placeholder='Name of Hospital'>

    <label for='street'>Street</label>
    <input
      id='street'
      v-model='street'
      type='text'
      placeholder='123 Street dr'>

    <label for='city'>City</label>
    <input id='city' v-model='city' type='text' placeholder='City'>

    <label for='state'>State</label>
    <select id='state' v-model='state'>
      <option value="" selected>-- Please Select --</option>
      <option
        v-for='state in states'
        :key='state.abbreviation'
        :value='state.abbreviation'>
        {{ state.name }}
      </option>
    </select>

    <button
      class='btn'
      @click='createHospital'
      :disabled='name.length === 0'>
      Create
    </button>
  </div>
</template>

<script>
import states from '../../public/states.json'
export default {
  name: 'CreateHospital',
  data: function() {
    return {
      name: '',
      hospitals: [],
      street: '',
      city: '',
      state: '',
      states: states,
    }
  },
  mounted: function() {
    this.$refs.name.focus()
  },
  methods: {
    createHospital: function() {
      this.hospitals.push(this.name)
      this.name = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0
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
