<template>
  <div>
    <div>
      <h1>Units list</h1>
        <h2>{{baseUnit}}</h2>
        <ul>
          <li v-for="Unit in Units" :key="Unit">
            <p>1 {{baseUnit}} =  {{Unit.formula}}  {{ Unit.name }}</p>
            <label>{{Value}} {{baseUnit}} = {{Value*Unit.formula}} {{Unit.name}}</label>
            <label></label>
          </li>
        </ul>
    </div>
    <div>
      <h3>Base Unit</h3>
        <label v-if="baseUnit !== ''">Value to convert</label>
        <input v-if="baseUnit !== ''" type="text" v-model="Value">
        <label>Base Unit</label>
        <input type="text" v-model="baseUnit">
      </form>
    </div>
    <div>
    <h3>New Unit</h3>
      <form @submit.prevent="addNewUnit()">
        <label>Unit name </label>
        <input type="text" v-model="newUnit.name">
        <label>Unit formula (multipplier based on base unit)</label>
        <input type="text" v-model="newUnit.formula"><br>
        <button>Add new Unit</button>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        Value: '',
        baseUnit: '',
        Units: [],
        newUnit: {
        },
      };
    },
    methods: {
      addNewUnit() {
        this.Units.push(this.newUnit);
        this.newUnit = {};
      }
    }
  };
</script>
