<template>
  <div id="app">
    JavaScript editor
    <Ace
      mode="javascript"
      theme="github"
      :content="contentJs"
      @content-changed="onChangeJs"
      style="height: 10rem"
    />

    Python editor
    <Ace
      mode="python"
      theme="terminal"
      :content="contentPython"
      @content-changed="onChangePython"
      style="height: 10rem"
    />

    <div class="box">
      <p>JavaScript content</p>
      <textarea
        v-model="contentJs"
        disabled
        class="preview"
      />
    </div>

    <div class="box">
      <p>Python content</p>
      <textarea
        v-model="contentPython"
        disabled
        class="preview"
      />
    </div>
  </div>
</template>

<script>
import Ace from './components/Ace.vue'

export default {
  name: 'App',
  components: {
    Ace
  },
  data() {
    return {
      contentJs: `var func = function() {
    alert('Hello world');
};

func();`,
      contentPython: `def func():
    print('Hello world')

func()`
    }
  },
  methods: {
    onChangeJs(data) {
      this.contentJs = data;
    },
    onChangePython(data) {
      this.contentPython = data;
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.box {
  display: inline-block;
  width: 20rem;
}

.preview {
  width: 100%;
  height: 10rem;
}
</style>
