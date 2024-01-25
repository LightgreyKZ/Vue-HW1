<template>
  <!-- в счетчик добавить кнопки прибавить/убавить, добавить ограничения -10/+10. При достижении этих чисел. выводить надпись, использовать для этого v-show. -->    
  <div>
    <button @click="inc()">INC</button>
    <button @click="dec()">DEC</button>
    <p>{{ Count }}</p>
    <p v-show="Count == 10||Count == -10">Достигнуто ограничение по счетчику!</p>
  </div>

  <!-- <div className="wrapper">
    <h1 :class="headingClass">{{ msg }}</h1>
    <h3 v-if="type === 'A'">A</h3>
    <h3 v-else-if="type === 'B'">B</h3>
    <h3 v-else-if="type === 'C'">C</h3>
    <h3 v-else>Not A\B\C</h3>

  </div> -->
  <input type="text" v-model="userName" placeholder="Имя">
  <input type="number" v-model="userAge" placeholder="Возраст">
  <input type="number" v-model="userBooks" placeholder="книги">
  <button type="button" @click="AddUser()">Добавить пользователя</button>
  <!-- <p v-if="users.length">{{ users }}</p> -->
  <ul>
    <li v-for="(item, index) in users" :key="index" :class="{redcolor: item.red}"><b>{{ item.name }}</b> - Возраст: {{ item.age }} - Книг: {{ item.books }}</li>
  </ul>
</template>


<script>
export default {
  data() {
    return {
      msg: "Test message",
      headingClass: "main-heading",
      // type: "A",
      // books: ['Book1','Book2','Book3','Book4','Book5','Book6','Book7','Book8','Book9','Book10'],
      users: [],
      userName: '',
      userAge: '',
      userBooks: '',
      userRed: false, //переменная для определения красного цвета
      Count: 0
    }
  },
  // mounted() {
  //   this.msg = "Updated message"
  // },
  methods: {
    inc() {
      if (this.Count == 10) {
        return;
      }
      this.Count++
    },
    dec() {
      if (this.Count == -10) {
        return;
      }
      this.Count--
    },
    AddUser() {
      if (this.userBooks == 0||this.userBooks > 10) {this.userRed = true}
        else this.userRed = false;
      this.users.push({
        name: this.userName,
        age: this.userAge,
        books: this.userBooks,
        red: this.userRed   
        });
    }
  }
}
 
</script>

<style>

.redcolor {
  color: red;
}

input {
  display: block;
  margin-bottom: 10px;
  font-size: 20px;
  height: 40px;
  padding: 5px;
  border: 1px solid rgba(128, 128, 128, 0.514);
  border-radius: 5px;
  outline: none;
  background: rgba(128, 128, 128, 0.384);
}

button[type="button"] {
  border: 0;
  border-radius: 5px;
  outline: none;
  padding: 10px 15px;
  background-color: #47e24c;
  color: #154716;
  font-weight: bold;
  transition: all 0.5s ease;
}

button[type="button"]:hover {
  transform: translateY(5px);
  background-color: white;
  border: 1px solid black;
}

p {
  transition: all 0.2s ease;
  font-size: 20px;
}

p::content {
  transform: rotateY(5px);
}

li {
  font-size: 20px;
}

</style>



<!-- в списке с пользователями и книгами - если у юзера 0 книг или больше 10 книг - выделить этот пункт красным цветом -->