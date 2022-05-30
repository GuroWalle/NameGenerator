<template>
  <div class="name-generator">
    <div class="name-generator__title">
      <h1>HELLO</h1>
      <h2>my name is:</h2>
    </div>

    <div class="name-generator__names">
      <h3>{{ firstName }}</h3>
      <h3>{{ lastName }}</h3>
    </div>

    <div class="name-generator__buttons">
      <button @click="fetchNewFirstName">
        Click for firstname
      </button>
      <button @click="fetchNewLastName">
        Click for lastname
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: "firstname",
      lastName: "lastname",
    };
  },

  methods: {
    async fetchNewFirstName() {
      const url = "https://randomuser.me/api/";
      const result = await fetch(url);
      const { results } = await result.json();
      this.firstName = `${results[0].name.first}`;
    },

    async fetchNewLastName() {
      const url = "https://randomuser.me/api/";
      const result = await fetch(url);
      const { results } = await result.json();
      this.lastName = `${results[0].name.last}`;
    },
  },
};
</script>

<style>
.name-generator {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}

.name-generator__title {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 60rem;
  height: 10rem;
  border-radius: 2rem 2rem 0 0;
  background: red;
  color: white;
}

.name-generator__title h1 {
  font-size: var(--font-heading);
}

.name-generator__title h2 {
  font-size: var(--font-body);
}

.name-generator__names {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  width: 60rem;
  height: 20rem;
  font-size: var(--font-body);
  background: white;
}

.name-generator__buttons {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  width: 60rem;
  height: 7rem;
  background: lightgray;
  border-radius: 0 0 1rem 1rem;
  font-size: var(--font-body);
}

.name-generator__buttons button {
  color: black;
}

.name-generator__buttons button:hover {
  text-shadow: 0.05rem 0.05rem black;
}
</style>