<template>
  <div class="expense-table">
    <div class="link-group">
      <p>Välj kategori:</p>
      <!-- On click change data in variable for if-else table-print -->
      <a href="javascript:;" v-on:click="categorySelected = null">Alla</a>
      <a href="javascript:;" v-on:click="categorySelected = 'Mat'">Mat</a>
      <a href="javascript:;" v-on:click="categorySelected = 'Hemmet'">Hemmet</a>
      <a href="javascript:;" v-on:click="categorySelected = 'Transport'">Transport</a>
      <a href="javascript:;" v-on:click="categorySelected = 'Roligt'">Roligt</a>
      <a href="javascript:;" v-on:click="categorySelected = 'Personligt'">Personligt</a>
      <a href="javascript:;" v-on:click="categorySelected = 'Annat'">Annat</a>
    </div>
    <!-- Variable to tell wich category-table to print -->
    <table v-if="categorySelected === 'Mat'">
      <tr>
        <th>Inköpsdatum</th>
        <th>Titel</th>
        <th>Pris</th>
        <th>Kategori</th>
        <th>Redigera</th>
      </tr>
      <!-- For-each expense in array and bind row to expense _id -->
      <tr v-for="(expense, i) in getCategory1" v-bind:key="expense._id">
        <!-- If variable is set to _id display input -->
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.date" />
        </td>
        <!-- Else display data -->
        <td v-else>{{ expense.date.slice(0, 10) }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.title" />
        </td>
        <td v-else>{{ expense.title }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.price" />
        </td>
        <td v-else>{{ expense.price }}</td>
        <td v-if="editExpense === expense._id">
          <select v-model="expense.category">
            <option value="Mat">Mat</option>
            <option value="Hemmet">Hemmet</option>
            <option value="Transport">Transport</option>
            <option value="Roligt">Roligt</option>
            <option value="Personligt">Personligt</option>
            <option value="Annat">Annat</option>
          </select>
        </td>
        <td v-else>{{ expense.category }}</td>
        <!-- If variable is set to _id display save button -->
        <td v-if="editExpense === expense._id">
          <button class="btn" v-on:click="updateExpense(expense)">Spara</button>
        </td>
        <!-- Else display edit and delete buttons -->
        <td class="btn-group" v-else>
          <button class="btn" v-on:click="editExpense = expense._id">Ändra</button>
          <button class="btn" v-on:click="deleteExpense(expense._id, i)">Radera</button>
        </td>
      </tr>
    </table>
    <!-- Repeat of same table, diffrent category -->
    <table v-else-if="categorySelected === 'Hemmet'">
      <tr>
        <th>Inköpsdatum</th>
        <th>Titel</th>
        <th>Pris</th>
        <th>Kategori</th>
        <th>Redigera</th>
      </tr>
      <tr v-for="(expense, i) in getCategory2" v-bind:key="expense._id">
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.date" />
        </td>
        <td v-else>{{ expense.date.slice(0, 10) }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.title" />
        </td>
        <td v-else>{{ expense.title }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.price" />
        </td>
        <td v-else>{{ expense.price }}</td>
        <td v-if="editExpense === expense._id">
          <select v-model="expense.category">
            <option value="Mat">Mat</option>
            <option value="Hemmet">Hemmet</option>
            <option value="Transport">Transport</option>
            <option value="Roligt">Roligt</option>
            <option value="Personligt">Personligt</option>
            <option value="Annat">Annat</option>
          </select>
        </td>
        <td v-else>{{ expense.category }}</td>
        <td v-if="editExpense === expense._id">
          <button class="btn" v-on:click="updateExpense(expense)">Spara</button>
        </td>
        <td class="btn-group" v-else>
          <button class="btn" v-on:click="editExpense = expense._id">Ändra</button>
          <button class="btn" v-on:click="deleteExpense(expense._id, i)">Radera</button>
        </td>
      </tr>
    </table>
    <!-- Repeat of same table, diffrent category -->
    <table v-else-if="categorySelected === 'Transport'">
      <tr>
        <th>Inköpsdatum</th>
        <th>Titel</th>
        <th>Pris</th>
        <th>Kategori</th>
        <th>Redigera</th>
      </tr>
      <tr v-for="(expense, i) in getCategory3" v-bind:key="expense._id">
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.date" />
        </td>
        <td v-else>{{ expense.date.slice(0, 10) }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.title" />
        </td>
        <td v-else>{{ expense.title }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.price" />
        </td>
        <td v-else>{{ expense.price }}</td>
        <td v-if="editExpense === expense._id">
          <select v-model="expense.category">
            <option value="Mat">Mat</option>
            <option value="Hemmet">Hemmet</option>
            <option value="Transport">Transport</option>
            <option value="Roligt">Roligt</option>
            <option value="Personligt">Personligt</option>
            <option value="Annat">Annat</option>
          </select>
        </td>
        <td v-else>{{ expense.category }}</td>
        <td v-if="editExpense === expense._id">
          <button class="btn" v-on:click="updateExpense(expense)">Spara</button>
        </td>
        <td class="btn-group" v-else>
          <button class="btn" v-on:click="editExpense = expense._id">Ändra</button>
          <button class="btn" v-on:click="deleteExpense(expense._id, i)">Radera</button>
        </td>
      </tr>
    </table>
    <!-- Repeat of same table, diffrent category -->
    <table v-else-if="categorySelected === 'Roligt'">
      <tr>
        <th>Inköpsdatum</th>
        <th>Titel</th>
        <th>Pris</th>
        <th>Kategori</th>
        <th>Redigera</th>
      </tr>
      <tr v-for="(expense, i) in getCategory4" v-bind:key="expense._id">
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.date" />
        </td>
        <td v-else>{{ expense.date.slice(0, 10) }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.title" />
        </td>
        <td v-else>{{ expense.title }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.price" />
        </td>
        <td v-else>{{ expense.price }}</td>
        <td v-if="editExpense === expense._id">
          <select v-model="expense.category">
            <option value="Mat">Mat</option>
            <option value="Hemmet">Hemmet</option>
            <option value="Transport">Transport</option>
            <option value="Roligt">Roligt</option>
            <option value="Personligt">Personligt</option>
            <option value="Annat">Annat</option>
          </select>
        </td>
        <td v-else>{{ expense.category }}</td>
        <td v-if="editExpense === expense._id">
          <button class="btn" v-on:click="updateExpense(expense)">Spara</button>
        </td>
        <td class="btn-group" v-else>
          <button class="btn" v-on:click="editExpense = expense._id">Ändra</button>
          <button class="btn" v-on:click="deleteExpense(expense._id, i)">Radera</button>
        </td>
      </tr>
    </table>
    <!-- Repeat of same table, diffrent category -->
    <table v-else-if="categorySelected === 'Personligt'">
      <tr>
        <th>Inköpsdatum</th>
        <th>Titel</th>
        <th>Pris</th>
        <th>Kategori</th>
        <th>Redigera</th>
      </tr>
      <tr v-for="(expense, i) in getCategory5" v-bind:key="expense._id">
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.date" />
        </td>
        <td v-else>{{ expense.date.slice(0, 10) }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.title" />
        </td>
        <td v-else>{{ expense.title }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.price" />
        </td>
        <td v-else>{{ expense.price }}</td>
        <td v-if="editExpense === expense._id">
          <select v-model="expense.category">
            <option value="Mat">Mat</option>
            <option value="Hemmet">Hemmet</option>
            <option value="Transport">Transport</option>
            <option value="Roligt">Roligt</option>
            <option value="Personligt">Personligt</option>
            <option value="Annat">Annat</option>
          </select>
        </td>
        <td v-else>{{ expense.category }}</td>
        <td v-if="editExpense === expense._id">
          <button class="btn" v-on:click="updateExpense(expense)">Spara</button>
        </td>
        <td class="btn-group" v-else>
          <button class="btn" v-on:click="editExpense = expense._id">Ändra</button>
          <button class="btn" v-on:click="deleteExpense(expense._id, i)">Radera</button>
        </td>
      </tr>
    </table>
    <!-- Repeat of same table, diffrent category -->
    <table v-else-if="categorySelected === 'Annat'">
      <tr>
        <th>Inköpsdatum</th>
        <th>Titel</th>
        <th>Pris</th>
        <th>Kategori</th>
        <th>Redigera</th>
      </tr>
      <tr v-for="(expense, i) in getCategory6" v-bind:key="expense._id">
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.date" />
        </td>
        <td v-else>{{ expense.date.slice(0, 10) }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.title" />
        </td>
        <td v-else>{{ expense.title }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.price" />
        </td>
        <td v-else>{{ expense.price }}</td>
        <td v-if="editExpense === expense._id">
          <select v-model="expense.category">
            <option value="Mat">Mat</option>
            <option value="Hemmet">Hemmet</option>
            <option value="Transport">Transport</option>
            <option value="Roligt">Roligt</option>
            <option value="Personligt">Personligt</option>
            <option value="Annat">Annat</option>
          </select>
        </td>
        <td v-else>{{ expense.category }}</td>
        <td v-if="editExpense === expense._id">
          <button class="btn" v-on:click="updateExpense(expense)">Spara</button>
        </td>
        <td class="btn-group" v-else>
          <button class="btn" v-on:click="editExpense = expense._id">Ändra</button>
          <button class="btn" v-on:click="deleteExpense(expense._id, i)">Radera</button>
        </td>
      </tr>
    </table>
    <!-- Repeat of same table, no category, all expenses sorted in computed value -->
    <table v-else>
      <tr>
        <th>Inköpsdatum</th>
        <th>Titel</th>
        <th>Pris</th>
        <th>Kategori</th>
        <th>Redigera</th>
      </tr>
      <tr v-for="(expense, i) in sortedExpenses" v-bind:key="expense._id">
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.date" />
        </td>
        <td v-else>{{ expense.date.slice(0, 10) }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.title" />
        </td>
        <td v-else>{{ expense.title }}</td>
        <td v-if="editExpense === expense._id">
          <input v-on:keyup.enter="updateExpense(expense)" v-model="expense.price" />
        </td>
        <td v-else>{{ expense.price }}</td>
        <td v-if="editExpense === expense._id">
          <select v-model="expense.category">
            <option value="Mat">Mat</option>
            <option value="Hemmet">Hemmet</option>
            <option value="Transport">Transport</option>
            <option value="Roligt">Roligt</option>
            <option value="Personligt">Personligt</option>
            <option value="Annat">Annat</option>
          </select>
        </td>
        <td v-else>{{ expense.category }}</td>
        <td v-if="editExpense === expense._id">
          <button class="btn" v-on:click="updateExpense(expense)">Spara</button>
        </td>
        <td class="btn-group" v-else>
          <button class="btn" v-on:click="editExpense = expense._id">Ändra</button>
          <button class="btn" v-on:click="deleteExpense(expense._id, i)">Radera</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "ExpenseTable",
  data() {
    return {
      expenses: [],
      editExpense: null,
      categorySelected: null
    }
  },
  //Get all expenses, parse JSON and assign data to array
  created() {
    fetch("https://glacial-crag-50043.herokuapp.com/expenses")
      .then((response) => response.json())
      .then((data) => {
        this.expenses = data;
      })
  },
  methods: {
    //Delete expense by _id, then remove same expense from array by index and reload
    deleteExpense(_id, i) {
      fetch("https://glacial-crag-50043.herokuapp.com/expenses/" + _id, {
        method: "DELETE",
      }).then(() => {
        this.expenses.splice(i, 1);
        location.reload()
      })
    },
    //Turn ecpense by _id to JSON and update, then reset variable for button-display in HTML
    updateExpense(expense) {
      fetch("https://glacial-crag-50043.herokuapp.com/expenses/" + expense._id, {
        body: JSON.stringify(expense),
        method: "PUT",
        headers: {
          "Content-Type": "application/json",
        },
      }).then(() => {
        this.editExpense = null;
      })
    }
  },
  computed: {
    //Sort expense array by date, new -> old
    sortedExpenses() {
      return this.expenses.slice().sort((a, b) => {
        return new Date(b.date) - new Date(a.date)
      })
    },
    //Sorted expense array filtered by category
    getCategory1: function () {
      return this.sortedExpenses.filter(function (expense) {
        return expense.category === "Mat"
      })
    },
    getCategory2: function () {
      return this.sortedExpenses.filter(function (expense) {
        return expense.category === "Hemmet"
      })
    },
    getCategory3: function () {
      return this.sortedExpenses.filter(function (expense) {
        return expense.category === "Transport"
      })
    },
    getCategory4: function () {
      return this.sortedExpenses.filter(function (expense) {
        return expense.category === "Roligt"
      })
    },
    getCategory5: function () {
      return this.sortedExpenses.filter(function (expense) {
        return expense.category === "Personligt"
      })
    },
    getCategory6: function () {
      return this.sortedExpenses.filter(function (expense) {
        return expense.category === "Annat"
      })
    }
  }
};
</script>

<!-- Style for this component only -->
<style scoped>
.link-group {
  display: flex;
  justify-content: space-between;
  margin: 10px 15px 20px 15px;
}
a {
  font-family: "Open Sans", Helvetica, sans-serif;
  color: rgb(66, 66, 66);
}
a:hover {
  color: rgb(168, 168, 168);
}
a:active {
  color: rgb(204, 204, 204);
}
.expense-table {
  border: 2px solid white;
  border-radius: 20px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-top: 20px;
  background-color: rgba(113, 224, 113, 0.288);
  margin-bottom: 60px;
}
table {
  width: 600px;
  border-collapse: collapse;
}
tr {
  width: 100%;
}
tr:nth-child(even) {
  background-color: #ffffff;
}
th {
  text-align: left;
  font-family: "Permanent Marker", Helvetica, sans-serif;
  letter-spacing: 0.02em;
  font-size: 1.2em;
  padding: 5px 10px;
}
td {
  padding: 5px 10px;
}
.btn-group {
  display: flex;
  flex-wrap: nowrap;
}
</style>