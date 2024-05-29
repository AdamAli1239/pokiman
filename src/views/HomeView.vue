<template>
  <div class="home">
    <h1>Pepsi Pokemon thing</h1>
    <p>
      I dont really know what else to put here tbh so ima just do random stuff
      to practice vue skill :3
    </p>
    <label>Input stuff into this text it does nothing tho tbh</label>
    <input type="text" v-model="wlatt" />
    <p>You inputted - {{ wlatt }}</p>
    <label>Click for option 1</label>
    <input type="checkbox" value="hi" v-model="mist" />
    <label>Click for option 2</label>
    <input type="checkbox" value="whats" v-model="mist" />
    <label>Click for option 3</label>
    <input type="checkbox" value="up" v-model="mist" />
    <label>Click for option 4</label>
    <input type="checkbox" value="pepsi" v-model="mist" />
    <label>Click for option 5</label>
    <input type="checkbox" value="want some" v-model="mist" />
    <label>Click for option 6</label>
    <input type="checkbox" value="water?" v-model="mist" />
    <p v-for="mis in mist" :key="mis">{{ mis }}</p>
    <h3>
      Enter random words I will make them not be able to duplicate, but hold
      down alt
    </h3>
    <input type="text" @keyup.alt="lahlah(e)" v-model="mo" />
    <p v-for="hi in second" :key="hi">{{ hi }}</p>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  components: {},
  data() {
    return {
      mo: "",
      wlatt: "",
      mist: [],

      second: [],
    };
  },
  methods: {
    lahlah(e) {
      if (this.mo && this.mo[-1] == ",") {
        console.log("afawd");
      }
    },
  },
};
</script>
