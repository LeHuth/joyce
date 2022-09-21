
<script>
      import {onMount} from 'svelte'
      import { fly,slide } from 'svelte/transition';
      import axios from 'axios';
      import List from '../lib/List.svelte'

  let users = []
  let page = 0
  let flyRight = true
  let loaded = false
  $: {
    console.log(users)
  }
  onMount(async () => {
    fetchUserList()
  })
  let fetchUserList = async (nextpage = 0) => {
    nextpage > page ? flyRight = true : flyRight = false
    loaded = false 
    const response = await axios.get(`https://dummyapi.io/data/v1/user?limit=12&page=${nextpage}`,{headers: {
      'app-id': '6324f52939ef30ae3a6285c4'
    }})
    
    users = response.data.data
    page = response.data.page
    
    loaded = true
  }
  function flyDirection(){
    return flyRight ? 100 : -100
  }
</script>
<main class="flex justify-between h-screen items-center flex-col">
    
   
    {#if loaded}
    <div in:fly={{x: flyDirection(), duration: 500}} out:fly={{x: flyDirection() * -1, duration: 500}} class='max-w-screen-lg'>
        <List users={users} />
    </div>
    {/if}
    <div class="flex gap-4 w-fit self-center">
        <button on:click={() => fetchUserList(page-1)}>previous page</button>
        <button on:click={()=> fetchUserList(page+1)}>next page</button>
    </div>
    
    
  </main>