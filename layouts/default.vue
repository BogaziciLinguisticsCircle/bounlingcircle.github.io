<template>
  <section>
    <aside>
      <h2>Boğaziçi University</h2>
      <h3>Lingustistics Circle</h3>
    </aside>
    <main>
      <Nuxt />
    </main>
    <footer>
      Made by Yankı Ekin Yüksel
    </footer>
  </section>
</template>

<script type="text/javascript">
  export default {
    name: "DefaultLayout"
  }
</script>

<style lang="scss">
html, body {
  background-color: #fafafa;
  font-family: "Fira Sans", sans-serif;
  font-weight: 300;
  font-size: 14px;
  margin: 0;
}
section {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  & > * {
    padding: 1em;
  }
  aside {
  }
  main {
    flex-shrink: 1;
  }
}
footer {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 1em;
  font-size: .75em;
  text-align: right;
}
.nuxt-content {
  p {
    white-space: break-spaces;
  }
}
</style>
