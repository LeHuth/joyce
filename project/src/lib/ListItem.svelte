<script>
    export let user
    import {push, pop, replace} from 'svelte-spa-router'
</script>

<div class='px-7 py-5 flex flex-start align-baseline shadow-grey-100 w-80 shadow-md border border-solid' on:click={()=> push(`/user/${user.id}`)}>
    <img class='aspect-square w-auto h-20 pr-2' src={user.picture} alt="profilepicture">
    <div class='flex flex-col justify-center'>
        <h3 class='text-xl capitalize text-clip'>{user.title} {user.firstName}</h3>
        <h1 class='text-4xl text-blue-500 text-clip'>{user.lastName}</h1>
    </div>
    
  </div>