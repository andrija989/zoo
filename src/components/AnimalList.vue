<template>
<div>
    <form @submit.prevent="addAnimal">
    <div>
      <label for="type">Animal type</label>
      <input type="text" id="type" v-model="newAnimal.type" required>
    </div>
    <div>
      <label for="name">Animal name</label>
      <input type="text" id="name" v-model="newAnimal.name" required>
    </div>
    <div>
      <label for="dateOfBirth">dateOfBirth</label>
      <input type="text" id="dateOfBirth" v-model="newAnimal.dateOfBirth" required>
    </div>

    <div>
      <button type="submit">Add Animal</button>
    </div>
  </form>
    <ul>
      <li v-for='(animal,index) in animals' :key="index">
        {{ animal.type }} {{ animal.name }} - {{ animal.dateOfBirth ? animal.dateOfBirth : "Nepoznat" }}
        <button @click="removeAnimal(index)">Remove Animal</button>
        <button @click="moveToTop(index)">Move to top</button>
      </li>
    </ul>
</div>
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

  methods: {
    removeAnimal(index) {
      this.animals.splice(index,1)
    },

    moveToTop(index) {
      let animalsCopy = this.animals[index]
      this.animals.splice(index,1)
      this.animals.unshift(animalsCopy)
    },

    addAnimal() {
      this.animals.push({...this.newAnimal})
      this.newAnimal = [
        type = "",
        name = "",
        dateOfBirth = ""
      ]
    }
  }
}
</script>


<style scoped>

</style>
