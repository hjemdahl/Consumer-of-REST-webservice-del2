<template>
    <div class="expense-input">
        <!-- In each input-group v-model binds the input to the variable,
        and if validation error exist print message -->
        <div class="input-group">
            <label for="date">ÅÅÅÅ-MM-DD</label>
            <input type="text" class="form-input" id="date" v-model="date"/>
            <span class="err-msg" v-if="v$.date.$error">{{ v$.date.$errors[0].$message }}</span>
        </div>
        <div class="input-group">
            <label for="title">Titel</label>
            <input type="text" class="form-input" id="title" v-model="title" />
            <span class="err-msg" v-if="v$.title.$error">{{ v$.title.$errors[0].$message }}</span>

        </div>
        <div class="input-group">
            <label for="price">Pris(kr.öre)</label>
            <input type="text" class="form-input" id="price" v-model="price" />
            <span class="err-msg" v-if="v$.price.$error">{{ v$.price.$errors[0].$message }}</span>
        </div>
        <div class="input-group">
            <label for="category">Kategori</label>
            <select class="form-input" id="category" v-model="category" name="category">
                <option value="Mat">Mat</option>
                <option value="Hemmet">Hemmet</option>
                <option value="Transport">Transport</option>
                <option value="Roligt">Roligt</option>
                <option value="Personligt">Personligt</option>
                <option value="Annat">Annat</option>
            </select>
            <span class="err-msg" v-if="v$.category.$error">{{ v$.category.$errors[0].$message }}</span>
        </div>
        <!-- Call method to add expense on click -->
        <button class="btn" v-on:click="addExpense">Lägg till</button>
    </div>
</template>

<script>
//For input validaton
import useValidate from '@vuelidate/core'
import { required, minLength, maxLength, minValue, maxValue, decimal } from '@vuelidate/validators'
export default {
    name: 'AddExpense',
    data() {
        return {
            v$: useValidate(),
            expenses: [],
            date: null,
            title: null,
            price: null,
            category: null
        }
    },
    validations() {
        return {
            //Assign validation data
            expenses: [],
            date: { required, minLength: minLength(10), maxLength: maxLength(10) },
            title: { required, minLength: minLength(1), maxLength: maxLength(35) },
            price: { required, decimal, minValue: minValue(1), maxValue: maxValue(1000000) },
            category: { required }
        }
    },
    methods: {
        /*Call validation, if no validation error fetch REST-webservice and post data from form and reload */        
        addExpense() {
            this.v$.$validate()
            if (!this.v$.$error) {
                fetch("https://glacial-crag-50043.herokuapp.com/expenses", {
                    body: JSON.stringify({
                        date: this.date,
                        title: this.title,
                        price: this.price,
                        category: this.category
                    }),
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json",
                    },
                }).then(() => {
                    location.reload()
                })
            }
        }
    }
}
</script>

<!-- Style for this component only -->
<style scoped>
.expense-input {
    border: 2px solid white;
    border-radius: 20px;
    padding: 20px;
    display: flex;
    margin-top: 20px;
    align-items: end;
    background-color: rgba(255, 192, 203, 0.384);
}
.input-group {
    margin: 10px 0;
    display: flex;
    flex-direction: column;
}
label {
    font-size: 0.8em;
    margin: 0 0 3px 3px;
}
.form-input {
    margin-right: 6px;
    border: none;
    padding: 3px 5px;
    border-radius: 6px;
    width: 120px;
    font-family: "Open Sans", Helvetica, sans-serif;
}
.btn {
margin-bottom: 12px;
}
.err-msg {
  color: brown;
  font-size: .8em;
  margin: 3px 0 0 3px;
  max-width: 110px;
}
</style>