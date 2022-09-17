<template>
  <div id="app">
    <KalkulatorView/>
  </div>
</template>

<script>
import KalkulatorView from './components/KalkulatorView.vue';

export default {
  name: 'App',
  components: {
    KalkulatorView
}
}
</script>

<style>
  body {
    background: #31475e;
  }

</style>
