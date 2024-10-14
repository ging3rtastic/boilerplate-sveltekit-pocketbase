<script lang="ts">
	// Components
	import LoggedIn from './LoggedIn.svelte';
	import LoggedOut from './LoggedOut.svelte';
	import ToggleLightDarkMode from './ToggleLightDarkMode.svelte';

	// Types and variables
	import { user } from '$lib/stores/user.store';
</script>

<div class="navbar">
	<div class="flex-1">
		<a href="/" class="text-xl btn btn-ghost">
			<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="size-5">
				<path fill-rule="evenodd" d="M9.293 2.293a1 1 0 0 1 1.414 0l7 7A1 1 0 0 1 17 11h-1v6a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1v-3a1 1 0 0 0-1-1H9a1 1 0 0 0-1 1v3a1 1 0 0 1-1 1H5a1 1 0 0 1-1-1v-6H3a1 1 0 0 1-.707-1.707l7-7Z" clip-rule="evenodd" />
			</svg>			  
		</a>
		<div class="flex-none">
			<ToggleLightDarkMode></ToggleLightDarkMode>
		</div>
	</div>

	{#if $user}
		{#if $user.avatar}
			<LoggedIn avatar={$user.avatar}></LoggedIn>
		{:else if $user.avatarUrl}
			<LoggedIn avatar={$user.avatarUrl}></LoggedIn>
		{:else}
			<LoggedIn avatar={undefined}></LoggedIn>
		{/if}
	{:else}
		<LoggedOut></LoggedOut>
	{/if}
</div>
