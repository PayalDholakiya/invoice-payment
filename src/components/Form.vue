<template>
  <h1>Finance Logger</h1>
  <Display :detail="arrayData" />
  <div class="form-data">
    <div>
      Type:
      <select id="my_select" v-model="formData.type">
        <option value="invoice" id="invoice">invoice</option>
        <option value="payment" id="payment">payment</option>
      </select>
    </div>
    <div style="padding-top:2px">
      To/Form:
      <input v-model="formData.form" type="text" class="input-data" id="form" />
    </div>
    <div style="padding-top:2px">
      Details:
      <input
        v-model="formData.details"
        type="text"
        class="input-data"
        id="details"
      />
    </div>
    <div style="padding-top:2px">
      Amount:
      <input
        v-model="formData.amount"
        type="text"
        class="input-data"
        id="amount"
      />
    </div>
    <div class="add">
      <button @click="add()" type="submit" value="Add" id="add">
        Add
      </button>
    </div>
  </div>
</template>
<script>
import Display from './Display'

export default {
  components: {
    Display,
  },
  name: 'Form',
  data() {
    return {
      arrayData: [],
      formData: {
        type: 'invoice',
        form: '',
        details: '',
        amount: '',
      },
    }
  },
  methods: {
    add() {
      if (
        this.formData.typetype == '' ||
        this.formData.form == '' ||
        this.formData.details == '' ||
        this.formData.amount == ''
      ) {
        alert('all the filed are required.')
      } else {
        this.arrayData.push({ ...this.formData })
        this.formData.type = 'invoice'
        this.formData.form = ''
        this.formData.details = ''
        this.formData.amount = ''
      }
    },
  },
}
</script>
<style scoped>
h1 {
  color: fuchsia;
}
.form-data {
  height: 20vh;
  background-color: rgb(204, 203, 203);
  display: flex;
  align-items: center;
  flex-direction: row;
  padding-left: 10%;
  padding-right: 10%;
  margin-left: 10%;
  margin-right: 10%;
}

.add button {
  height: 30px;
  width: 90px;
  background-color: magenta;
  border-radius: 5px;
}
.add {
  padding-top: 2px;
  margin-left: 5%;
}
@media screen and (max-width: 1063px) {
  .form-data {
    display: flex;
    flex-direction: column;
    margin-left: 20%;
    margin-right: 20%;
    padding-top: 20px;
  }
  .add button {
    height: 30px;
    width: 90px;
  }
}
</style>
