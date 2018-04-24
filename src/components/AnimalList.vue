<template>
  <div>

    <form @submit.prevent="addAnimal">
      <label>Species</label>
      <input v-model="newAnimal.species" type='text' placeholder="species"/>
      <label>Name</label>
      <input v-model="newAnimal.name" type='text' placeholder="Name"/>
      <label>Day of birth</label>
      <input v-model="newAnimal.birth" type="text" placeholder="day of birth"/>
      <button type='submit'>Add Animal</button>
    </form>

    <table>
      <thead>
        <th>Species</th>
        <th>Name</th>
        <th>Sector</th>
        <th>Day of Birth</th>
        <th>&nbsp;</th>
      </thead>
      <tbody>
        <tr v-for= "(animal, key) in animals" :key="key">
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.sector.name }}</td>
          <td v-if="animal.birth === ''">Nepoznat</td>
          <td v-else>{{ animal.birth }}</td>
          <td>
            <button @click="removeAnimal(animal)">Remove</button>
          </td>
          <td>
            <button @click="moveToTop(animal)">Move to the top</button>
          </td>
        </tr>
      </tbody>
    </table>

    <table>
      <thead>
        <th>Name</th>
        <th>Surface</th>
      </thead>
      <tbody>
        <tr v-for = "(sector, key) in sectors" :key="key">
        <td>{{ sector.name }}</td>
        <td> {{ sector.surface }}</td>
        <td>
          <button @click="see(sector)">See list</button>
        </td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
const sectors = [
  { name:'Predators', surface: 'kage' },
  { name: 'WaterAnimals', surface: 'water' },
  { name: 'Fawl', surface: 'kage' }
];

export default {
  name: 'AnimalList',
  data() {
    return {
      sectors: sectors,
      animals:[
    { species: 'pas', name:'rex', birth:'1.1.2017.',sector:sectors[1]},
    { species: 'macka', name:'kitty', birth:'1.2.2017.',sector:sectors[0]},
    { species: 'papagaj', name:'koki', birth:'1.3.2017.',sector:sectors[0]},
    { species: 'zmija', name:'paja', birth:'1.4.2017.',sector:sectors[0]},
    { species: 'zec', name:'flafi', birth:'',sector:sectors[1]}
    ],
    newAnimal: {
        species: '',
        name: '',
        birth: ''
      }
      }},
    methods:{
       addAnimal(){
        this.animals.push(this.newAnimal),
        this.newAnimal= {}
      },
      removeAnimal(animal) {
        this.animals.splice(this.animals.indexOf(animal), 1)
      },
      moveToTop(animal){
        var arr = this.animals.splice(this.animals.indexOf(animal), 1)
        this.animals.unshift(arr[0])
      },
      see(sector){
        var indexAnimal=[]
        this.animals.forEach(animal => {
          if(animal.sector.name === sector.name)
            indexAnimal.push(animal.name)
      })
      alert(indexAnimal);
      }
     
    }
}
</script>


<style scoped>
h3 {
  margin: 40px 0 0;
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
/* vrstu, ime i datum rođenja */