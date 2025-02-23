<template>
  <header class="header">
    <div class="container">
      <div class="header__body">
        <nuxt-link to="/" class="header__logo">TEST TASK</nuxt-link>
      </div>
    </div>
  </header>
</template>

<script >

</script>

<style>

.header {
  background: var(--blue-light);
  padding: 2rem 0;
  box-shadow: 0 0 1.5rem .5rem #e8e8e8;
}

.header__body {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 2rem;
}

.header__logo {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  font-weight: 600;
  letter-spacing: 0.15rem;
  color: var(--text-color-primary);

  &:hover {
    color: var(--text-color-primary-hover);
  }
}

</style>
