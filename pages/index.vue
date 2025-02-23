<template>
  <section>
    <h1>Пользователи</h1>
    <ul class="users-list">
      <li v-for="user of users" :key="user.id">
        <nuxt-link :to="`${user.id}`">{{user.name}}</nuxt-link>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  async fetch({store}) {
    if (store.getters['users/users'].length === 0) {
      await store.dispatch('users/fetch')
    }
  },
  data: () => ({
    pageTitle: 'Users page'
  }),
  computed: {
    users() {
      return this.$store.getters['users/users']
    }
  },
  methods: {
  }
}
</script>

<style>

h1 {
  margin: 0 0 2rem 0;
}

.users-list {
  display: flex;
  align-items: stretch;
  flex-wrap: wrap;
  gap: 1rem;

  li {
    flex: 1 1 24%;
    background-color: var(--bg-dark);
    border-radius: var(--border-radius);
    transition: background-color var(--transition);

    &:hover {

      background-color: var(--blue-light);

      a {
        color: var(--text-color-primary);
      }
    }


    a {
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 1rem 2rem;
      font-size: 1.6rem;
      color: var(--text-color-light);
      font-weight: 500;
    }
  }
}

</style>
