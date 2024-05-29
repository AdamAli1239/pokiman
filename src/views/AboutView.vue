<template>
  <div class="about">
    <h1>Random pokemon page</h1>
    <button @click="getID">
      click to get a random pokemon (you have no say in which)
    </button>
    <p>Pokemon name: {{ pokeName }}</p>
    <p>Pokemon Evolution: {{ pokeEvo }}</p>
    <p>Pokemon Stats: {{ pokeStats }}</p>
  </div>
</template>
<script>
// @ is an alias to /src

export default {
  components: {},
  data() {
    return {
      id: null,
      pokeName: "",
      pokeStats: "",
      pokeEvo: "",
    };
  },
  methods: {
    getID() {
      this.id = Math.floor(Math.random() * 101);

      this.fetchdapoki().then((data) => {
        console.log("resolved", data);
        this.pokeName = data.chain.species.name;
        console.log(data.chain);

        // console.log(data.chain.species.name);
        // console.log(data.chain.evolves_to[0].species.name);
        if (data.chain.evolves_to.length != 0) {
          this.pokeEvo = data.chain.evolves_to[0].species.name;
        } else {
          this.pokeEvo = "No evolution left";
        }
      });
    },
    async fetchdapoki() {
      console.log("wagwan");

      const rand = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.id}/`);
      const ev = await fetch(
        `https://pokeapi.co/api/v2/evolution-chain/${this.id}/`
      );
      const evsec = await ev.json();
      const sec = await rand.json();
      return sec, evsec;
    },
  },
};
</script>
