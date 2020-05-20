<template>
  <div class="container">
    <div class="border border-secondary rounded m-auto p-3" >
      <h1 class="pb-2">Conversions</h1>
      <div class="card card border-light mb-3 " v-for="Unit in Units" :key="Unit" >
          <div class="card-header">
          <h5 class="font-weight-bold">{{Unit.name}} </h5>
          </div>
          <div class="card-body" >
            <p>1 {{baseUnit}} =  {{Unit.formula}}  {{ Unit.name }}</p>
            <p class="font-weight-bold"> {{Value}} {{baseUnit}} = {{Value*Unit.formula}} {{Unit.name}}</p>
          </div>
        </div>
    </div>
    <div class="border border-secondary rounded m-auto p-3">
      <h3>Base Unit</h3>
      <div class="m-2">
        <label>Base Unit</label>
        <input class="form-control" type="text" v-model="baseUnit">
      </div>
      <div class="m-2">
        <label v-if="baseUnit !== ''">Value to convert</label>
        <div class="input-group">
          <input class="form-control" v-if="baseUnit !== ''" type="text" v-model="Value">
          <div class="input-group-append">
            <span v-if="baseUnit !== ''" class="input-group-text" id="basic-addon2">{{baseUnit}}</span>
          </div>
        </div>
      </div>
    </div>
    <div class="border border-secondary rounded p-3">
    <h3>New Unit</h3>
      <form @submit.prevent>
      <div class="m-2">
        <label>Unit name </label>
        <input class="form-control" type="text" v-model="newUnit.name">
      </div>
      <div class="m-2">
        <label>Unit formula (multipplier based on base unit)</label>
        <input class="form-control" type="text" v-model="newUnit.formula"><br>
      </div>
      <div class="d-flex justify-content-md-center">
        <button @click="addNewUnit()" class="btn btn-outline-primary m-1">Add new unit</button>
        <button @click="resetUnits()" class="btn btn-outline-danger m-1">Reset units </button>
      </div>
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
      },
      resetUnits(){
        this.Units = this.Units.splice();
      }
    }
  };
</script>
