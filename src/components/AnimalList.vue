<template>
  
    <ul>
      <li v-for='(animal,index) in animals' :key="index">
        {{ animal.type }} {{ animal.name }} - {{ animal.dateOfBirth ? animal.dateOfBirth : "Nepoznat" }}
      </li>
    </ul>
  
</template>

<script>
export default {
  data() {
    return {
      newAnimal: {
        type:'',
        name:'',
        dateOfBirth:''
      },

      animals: [
        { type: 'Lion', name: 'Joe', dateOfBirth: '08/08/2018' },
        { type: 'Seal', name: 'Jack', dateOfBirth: '07/07/2013' },
        { type: 'Pidgeon', name: 'Mc', dateOfBirth: '05/05/1988' },
        { type: 'Frog', name: 'Kreu', dateOfBirth: '' },
        { type: 'Crow', name: 'Lorry', dateOfBirth: '02/02/1988' }
      ]
    }
  },
}
</script>


<style scoped>

</style>
