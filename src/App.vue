<template>
  <div id="app">
    <div>Enter anything, only alphabets and numbers will be accepted:</div>
    <div>
      <input
        class="NPInputValueField"
        type="text"
        name="inputValue"
        v-model="inputValue"
        @keydown="checkKeyDownAlphaNumeric($event)"
      />
    </div>
    <div v-if="inputValue" class="NPInputResponseContainer">
      Validated value: <strong>{{ inputValue }}</strong>
    </div>
    <div v-if="ignoredValue" class="NPInputResponseContainer">
      Ignored character: <strong>{{ ignoredValue }}</strong>
    </div>
    <div style="margin-top: 22px">
      <small>www.nightprogrammer.com</small>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      inputValue: "",
      ignoredValue: "",
    };
  },
  methods: {
    checkKeyDownAlphaNumeric(event) {
      if (!/[a-zA-Z0-9\s]/.test(event.key)) {
        this.ignoredValue = event.key ? event.key : "";
        event.preventDefault();
      }
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 14px;
}
.NPInputValueField {
  padding: 6px 10px;
  width: 200px;
  font-size: 14px;
  margin-top: 12px;
}
.NPInputResponseContainer {
  margin: 14px 0px;
  padding: 4px 8px;
  border: 1px solid rgb(150, 150, 150);
  background: #eee;
  max-width: 300px;
}
</style>
