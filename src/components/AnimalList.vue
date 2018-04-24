<template>
  <div>
    
    <table>
      <thead>
        <th>Species</th>
        <th>Name</th>
        <th>Day of Birth</th>
        <th>&nbsp;</th>
      </thead>
      <tbody>
        <tr v-for= "(animal, key) in animals" :key="key">
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td v-if="animal.birth === ''">Nepoznat</td>
          <td v-else>{{ animal.birth }}</td>
          <td>
            <button @click="removeAnimal(animal)">Remove</button>
          </td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data() {
    return { animals:[
    { species: 'pas', name:'rex', birth:'1.1.2017.'},
    { species: 'macka', name:'kitty', birth:'1.2.2017.'},
    { species: 'papagaj', name:'koki', birth:'1.3.2017.'},
    { species: 'zmija', name:'paja', birth:'1.4.2017.'},
    { species: 'zec', name:'flafi', birth:''}
    
    ]}},
    methods:{
      removeAnimal(animal) {
        this.animals.splice(this.animals.indexOf('animal'), 1)
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