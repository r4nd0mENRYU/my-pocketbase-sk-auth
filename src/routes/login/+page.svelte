<script lang="ts">
	import { applyAction, enhance } from "$app/forms";
	import { pb } from "$lib/pocketbase";



</script>

<form method="POST" class="card" use:enhance={({form, data, action}) => {
    
    return async ({result}) => { 
        pb.authStore.loadFromCookie(document.cookie);
        await applyAction(result);
    }
}}>
	<h1 class="text-2xl mb-8">Log in</h1>
	<div class="form-control gap-2 mb-4">
		<input type="email" class="input input-bordered" placeholder="Email" name="email" />
		<input type="password" class="input input-bordered" placeholder="Passowrd" name="password" />
	</div>
	<button class="btn btn-primary">Log in</button>
</form>
