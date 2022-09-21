<script>
  import axios from 'axios'
  import TailwindCss from './lib/TailwindCSS.svelte';
  import Router, {location, link} from 'svelte-spa-router';
  import Home from './pages/Home.svelte'
  import UserDetail from './pages/UserDetail.svelte';
  import {onMount} from 'svelte'

  
</script>
<TailwindCss/>
<Router routes={{
  '/': Home,
  '/user/:userID': UserDetail
}}/>

<style>
</style>
