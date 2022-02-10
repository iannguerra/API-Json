<template>
      <div id="nav">
          <router-link to="/" id="logo-url">
              <img src="logo" :alt="alt"  id="logo">
            </router-link>
    <router-link to="/">Cadastro</router-link> |
    <router-link to="/lista">Lista</router-link>
  </div>
</template>
<script>
export default {
    name: "Navbar",
    props: ["logo","alt"]
}
</script>

<style scoped>
    #nav {
        background: color solid #222;
        border-bottom: 4px solid #FCBA03;
        padding: 15px 50px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }

    #logo-url{
        margin: auto;
        margin-left: 0px;
    }

    #logo {
        width: 40px;
        height: 40px;
    }

    #nav a{
        color: #FCBA03;
        text-decoration: none;
        margin: 12px;
        transition: .5s;
    }

    #nav a:hover{
        color:aliceblue;
    }
</style>