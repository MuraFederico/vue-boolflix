<template>
  <header>
      <h1>BOOLFLIX</h1>
      <nav>
          <input type="text" placeholder="Search by Name">
          <button>Cerca</button>
      </nav>
  </header>
</template>

<script>
export default {
    name: 'HeaderNotflix',
}
</script>

<style lang="scss" scoped>
    header {
        padding: 1.5rem;
        display: flex;
        justify-content: space-between;
        background-color: black;
        h1 {
            color: red;
        }
        input {
            padding: 1rem;
            margin-right: .5rem;
        }
        button {
            padding: 1rem;
            background-color: red;
            border: none;
            border-radius: .2rem;
        }
    }
</style>>