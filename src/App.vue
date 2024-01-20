<script>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'

export default {
  components: {
    HelloWorld,
    RouterLink,
    RouterView
  },
  data() {
    return {
      msg: "Исходное сообщение!",
      headingClass: "main-heading",
      type: "C",
      count: 0,
      books: ['book 1', 'book 2', 'book 3', 'book 4'],
      users: [
        {
          name: 'Пользователь 1',
          age: 23,
          books: 11
        },
        {
          name: 'Пользователь 2',
          age: 23,
          books: 3
        },
        {
          name: 'Пользователь 3',
          age: 25,
          books: 20
        },
        {
          name: 'Пользователь 4',
          age: 27,
          books: 5
        },
        {
          name: 'Пользователь 5',
          age: 27,
          books: 0
        },
      ]
    }
  },
  mounted() {
    console.log(this.msg)
    this.msg = "Кнопки счетчика!"
    console.log(this.count)
  },
  methods: {
    increment() {
      if (this.count < 10) {
        this.count++
      }
    },
    decrement() {
      if (this.count > -10) {
        this.count--
      }
    }
  }
}

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">

      <!-- Заданаие счетчика -->
      <h1 :class="headingClass">{{ msg }}</h1>
      <button @click="increment()">Увеличить число</button>
      <button @click="decrement()">Уменьшить число</button>
      <h1>{{ count }}</h1>
      <h2 v-show="count === 10 || count === -10">Нельзя дальше!</h2>


      <!-- Задание выделение кол-ва книг -->
      <ul>
        <li v-for="(user, index) in users" :key="index" :class="{ 'red-text': user.books === 0 || user.books > 10 }">
          {{ user.name }} - Количество книг: {{ user.books }}
        </li>
      </ul>

      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

.red-text {
  color: red;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
