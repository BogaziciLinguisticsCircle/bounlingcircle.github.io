<template>
  <section>
  	<header> 
  		<NuxtLink to="/index">
  			Home
  		</NuxtLink>
  	</header>
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
  flex-flow: row wrap;
  justify-content: center;
  align-items: center;
  height: 100vh;
  & > * {
    padding: 1em;
  }
  main {
    flex-shrink: 1;
  }
}
header {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  padding: 1em;
  text-align: center;
  font-weight: bolder;
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
  table {
    width: 100%;
    text-align: left;
    thead {
      border-bottom: 1px solid darkgray;
    }
  }
}
</style>
