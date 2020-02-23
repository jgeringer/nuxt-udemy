<template>
  <div>
    <Header @sidenavToggle="displaySidenav = !displaySidenav" />
    <Sidenav
      :show="displaySidenav"
      @close="displaySidenav = false" />
    <nuxt/>
    <Footer />
  </div>
</template>

<script>
  import Header from '@/components/Navigation/Header'
  import Sidenav from '@/components/Navigation/Sidenav'
  import Footer from '@/components/Navigation/Footer'

  export default {
    // middleware: 'log',
    components: {
      Header,
      Sidenav,
      Footer
    },
    data() {
      return {
        displaySidenav: false
      }
    }
  }
</script>

<style>
.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
