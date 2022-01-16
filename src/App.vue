<template>
  <div class="app-container">
    <h1>Utgiftskollen</h1>
    <AddExpense />
    <ExpenseTable />
  </div>
</template>

<script>
import ExpenseTable from './components/ExpenseTable.vue'
import AddExpense from './components/AddExpense.vue'


export default {
  name: 'App',
  components: {
    ExpenseTable,
    AddExpense
  }
}
</script>

<!-- Style for whole app -->
<style>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&family=Permanent+Marker&display=swap");

* {
  margin: 0;
}
body {
  font-family: "Open Sans", Helvetica, sans-serif;
  color: rgb(66, 66, 66);
  font-size: 0.9em;
  background: rgb(238, 238, 238);
  width: 100%;
  display: flex;
  justify-content: center;
  padding-top: 6%;
}
h1 {
  font-family: "Permanent Marker", Helvetica, sans-serif;
  font-size: 3em;
  padding-left: 20px;
}
.btn {
  margin: 0 3px;
  padding: 1px 7px;
  font-family: "Open Sans", Helvetica, sans-serif;
  border: 1px solid  rgb(66, 66, 66);
  border-radius: 5px;
  background-color: white;
  max-height: 22px;
}
.btn:hover {
  background-color: rgb(238, 238, 238);
}
.btn:active {
  background-color: white;
}
</style>
