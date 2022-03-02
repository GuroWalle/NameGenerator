<template>
  <div class="name-generator">
    <div class="name-generator__title">
      <h1>HELLO</h1>
      <h2>my name is:</h2>
    </div>

    <div class="name-generator__names">
      <h3 class="names__fistname">{{ firstName }}</h3>
      <h3 class="names__lastname">{{ lastName }}</h3>
    </div>

    <div class="name-generator__buttons">
      <button class="button__fistname" @click="fetchNewFirstName">
        Click for firstname
      </button>
      <button class="button__lastname" @click="fetchNewLastName">
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
  margin: var(--size--big) 0 auto 0;
}

.name-generator__title {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 9rem;
  margin: 0 10rem;
  font-size: var(--font--heading);
  background: red;
  color: white;
  border-radius: 2rem 2rem 0 0;
}

.name-generator__title,
h2 {
  font-size: var(--font--caption);
}

.name-generator__names {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  margin: var(--size--big);
  font-size: var(--font--body);
}

.name-generator__buttons {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  font-size: var(--font--body);
  margin: 0 10rem;
  padding: 1rem;
  background: #ccc;
  border-radius: 0 0 1rem 1rem;
}

.name-generator__buttons,
button {
  color: black;
}

.button__fistname:hover,
.button__lastname:hover {
  text-shadow: 0.05rem 0.05rem black;
}
</style>