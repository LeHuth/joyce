
<script>
    export let users
    import ListItem from './ListItem.svelte'
</script>
<div class='flex flex-wrap gap-5'>
    {#each users as user(user.id)}
        <ListItem user={user} />
    {/each}
</div>
