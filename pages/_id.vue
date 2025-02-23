<template>
  <section class="user-card">
    <h1>{{ user.name }} <span>({{ user.username }})</span></h1>
    <div class="user-card__flex">
      <div class="user-card__col">
        <a :href="`mailto:${user.email}`">
          <span>Email:</span>
          <span>{{ user.email }}</span>
        </a>
        <a :href="`tel:+${user.phone}`">
          <span>Phone:</span>
          <span>{{ user.phone }}</span>
        </a>
        <a :href="`${user.website}`">
          <span>Site:</span>
          <span>{{ user.website }}</span>
        </a>
      </div>
      <div class="user-card__col">
        <p v-for="[key, value] of Object.entries(user.company)" :key="key">
          <span>{{ key }}:</span>
          <span>{{ value }}</span>
        </p>
      </div>
      <div class="user-card__col">
        <a target="_blank"
           :href="`https://yandex.ru/maps/?whatshere[point]=${user.address.geo.lng},${user.address.geo.lat}&whatshere[zoom]=17`">
          {{ `${user.address.city}, ${user.address.street}, ${user.address.suite}` }}
        </a>
      </div>
    </div>
    <div class="user-card__back">
      <nuxt-link class="style-btn" to="/">Назад</nuxt-link>
    </div>
  </section>
</template>

<script>
export default {
  validate({params}) {
    return /^\d+$/.test(params.id)
  },
  async asyncData({$axios, params}) {
    const user = await $axios.$get('https://jsonplaceholder.typicode.com/users/' + params.id)

    return {user}
  }
}
</script>


<style>

.user-card {

}

.user-card__flex {
  display: flex;
  align-items: stretch;
  flex-wrap: wrap;
  gap: 2rem;
}

.user-card__col {
  display: flex;
  flex-direction: column;
  gap: .5rem;
  padding: 1rem;
  border-radius: var(--border-radius);
  overflow: hidden;
  background-color: var(--blue-light);
  min-width: 28rem;

  &:nth-child(1) {
    flex: 1 1 47%;
  }

  &:nth-child(2) {
    flex: 1 1 47%;
  }

  &:nth-child(3) {
    flex: 1 1 100%;
  }

  a, p {
    color: inherit;
    font-size: 1.6rem;
    display: inline-flex;
    align-items: flex-start;
    gap: 1rem;
  }

  span {
    transition: color var(--transition);

    &:nth-child(1) {
      font-weight: 300;
    }

    &:nth-child(2) {
    }

  }

  a {

    &:hover {

      span {

        &:nth-child(1) {
          font-weight: 300;
        }

        &:nth-child(2) {
          color: var(--text-color-primary-hover);
        }

      }
    }

    span {
      transition: color var(--transition);

      &:nth-child(1) {
        font-weight: 300;
      }

      &:nth-child(2) {
      }

    }

  }
}

.user-card__back {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 2rem auto 0 auto;

  a {
    transition: transform var(--transition);
    background-color: var(--blue-light);
    font-weight: 500;
    text-transform: uppercase;

    &:hover {
      transform: scale(1.1);
    }
  }
}

</style>
