<script>
    import {onMount} from 'svelte'
    import axios from 'axios'

   import {location, pop} from 'svelte-spa-router'
   let userDetail = {}
   let userLocation = {}
   export let params = {}
   $: {
       console.log(userDetail)
   }
   onMount(async ()=> {
       const response = await axios.get(`https://dummyapi.io/data/v1/user/${params.userID}`, {headers: {
           'app-id': '6324f52939ef30ae3a6285c4'
       }})
       userDetail = response.data
       userLocation = userDetail.location
   })
</script>
<button class='bg-neutral-600 p-2' on:click={()=> pop()}>back</button>
<p>The current page is: {$location}</p>
<b>{params.userID}</b>

<p>{userDetail.dateOfBirth}</p>
<p>{userDetail.email}</p>
<p>{userDetail.gender}</p>
<p>{userDetail.phone}</p>
<p>{userDetail.registrationDate}</p>

<p>{userLocation.city}</p>
<p>{userLocation.country}</p>
<p>{userLocation.state}</p>
<p>{userLocation.street}</p>