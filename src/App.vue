<template>
  <div id="app">
    <b-navbar>
      <template slot="brand">
        <b-navbar-item tag="router-link" :to="{ path: '/' }"> </b-navbar-item>
      </template>
      <template slot="start">
        <b-navbar-item href="/">
          Home
        </b-navbar-item>
      </template>
    </b-navbar>
    <router-view />
  </div>
</template>

<style lang="scss">
table td,
table th {
  text-align: center !important;
}
</style>
