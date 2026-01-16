<script>
	import Social from '../atoms/Social.svelte';
	import { user } from '../../util/discord';

	import { GitHubIcon } from '@indaco/svelte-iconoir/github';
	import { DiscordIcon } from '@indaco/svelte-iconoir/discord';
	import { MailIcon } from '@indaco/svelte-iconoir/mail';
	import { CoffeeCupIcon } from '@indaco/svelte-iconoir/coffee-cup';
	import { LinkedInIcon } from '@indaco/svelte-iconoir/linkedin';
	import InstagramIcon from '../icons/InstagramIcon.svelte';
</script>

<div class="socials-container">
	<Social tip="Ojasvisharma26" link="http://github.com/Ojasvisharma26">
		<GitHubIcon color="var(--accent)" />
	</Social>

	<Social tip="@26_Ojasvi" link="https://www.instagram.com/26_ojasvi/">
	<InstagramIcon color="var(--accent)" />
</Social>


	<Social tip={user.username} link={`https://discord.com/users/${user.id}`}>
		<DiscordIcon color="var(--accent)" />
	</Social>

	<Social
	tip="ojasvisharma193@gmail.com"
	link="https://mail.google.com/mail/?view=cm&fs=1&to=ojasvisharma193@gmail.com"
>
	<MailIcon color="var(--accent)" />
</Social>

	<Social tip="26_Ojasvi" link="https://ko-fi.com/26_ojasvi">
		<CoffeeCupIcon color="var(--accent)" />
	</Social>
</div>

<style>
	.socials-container {
		display: flex;
		gap: 0.75rem;
	}
</style>
