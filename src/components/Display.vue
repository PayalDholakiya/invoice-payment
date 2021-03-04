<template>
  <div class="display">
    <div class="data" v-show="detail.length" v-for="(data, index) in detail">
      <h4>{{ data.type }}</h4>
      <p>
        {{ data.form }} is owed $ {{ data.amount }} for {{ data.details }} .
        <button @click="deleteItem(index)">delete</button>
      </p>
    </div>
  </div>
</template>
<script>
import Form from './Form'
export default {
  name: 'Display',
  props: {
    detail: {
      type: Array,
      default: null,
    },
  },
  components: {
    Form,
  },
  methods: {
    deleteItem(index) {
      this.detail.splice(index, 1)
    },
  },
}
</script>
<style scoped>
h1 {
  color: fuchsia;
}
.display {
  height: 40vh;
  width: 100%;
  overflow-y: scroll;
}
.data {
  margin-left: 20%;
  margin-right: 20%;
  margin-top: 5px;
  padding-left: 5px;
  border: 1px solid gainsboro;
  border-radius: 5px;
}
h4 {
  text-align: start;
  color: fuchsia;
}
p {
  text-align: start;
}
p button {
  text-align: end;
}
</style>
