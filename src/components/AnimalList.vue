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
    <select v-model="newAnimal.sector">
      <option disabled value="">Please select animal</option>
      <option v-for="(sector,index) in sectors" :key="index">
        {{sector}}
      </option>
      
    </select>
    <div>
      <button type="submit">Add Animal</button>
    </div>
  </form>
    <ul>
      <li v-for='(animal,index) in animals' :key="index">
        {{ animal.type }} {{ animal.name }} - {{ animal.dateOfBirth ? animal.dateOfBirth : "Nepoznat" }} - {{animal.sector}}
        <button @click="removeAnimal(index)">Remove Animal</button>
        <button @click="moveToTop(index)">Move to top</button>
      </li>
    </ul>
    <div>
    <ul>
        <li v-for="(sector,index) in sectors" :key="index">
            {{ sector }}
        <button @click="showAnimalsSector(sector)">Vidi listu zivotinja </button>
        </li>
    </ul>
    </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      newAnimal: {
        type:'',
        name:'',
        dateOfBirth:'',
        sector:''
      },

      sectors: [
        "zglavkari","glavonosci","sisari","ribe","ptice"
      ],

      animals: [
        { type: 'Lion', name: 'Joe', dateOfBirth: '08/08/2018', sector:"sisari" },
        { type: 'Seal', name: 'Jack', dateOfBirth: '07/07/2013', sector:"ptice" },
        { type: 'Pidgeon', name: 'Mc', dateOfBirth: '05/05/1988', sector:"ribe" },
        { type: 'Frog', name: 'Kreu', dateOfBirth: '', sector:"sisari" },
        { type: 'Crow', name: 'Lorry', dateOfBirth: '02/02/1988', sector:"zglavkari" }
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
    },

     showAnimalsSector (sector) {
      let sectorAnimals = this.animals.filter(animal => animal.sector === sector).map(animal=>animal.name);

      
      window.alert(sectorAnimals.join(', '))
    },

  }
}
</script>


<style scoped>

</style>
