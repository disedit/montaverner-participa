<template>
  <b-navbar toggleable type="dark" variant="primary" fixed="top">
    <a class="navbar-brand" href="/">
      {{ appName }}
      <span class="location">
        <i class="far fa-map-marker-alt" aria-hidden="true"></i> {{ user.name }}
      </span>
    </a>

    <form method="post" action="/logout">
      <input type="hidden" name="_token" :value="csrfToken" />
      <button type="submit" class="dropdown-item"><i class="far fa-sign-out-alt" aria-hidden="true"></i> Tanca sessió</button>
    </form>
  </b-navbar>
</template>

<script>
  export default {
    name: 'navbar',

    data() {
      return {
        appName: '',
        user: { name: '' },
        csrfToken: ''
      }
    },

    mounted() {
      this.appName = window.app.name;
      this.user = window.app.user;
      this.csrfToken = document.head.querySelector('meta[name="csrf-token"]').content;
    }
  }
</script>

<style lang="scss" scoped>
  .location {
    margin-left: 1rem;
    opacity: 0.6;
  }
</style>
