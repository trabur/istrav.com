<script lang="ts">
	import { page } from '$app/stores';

	let name = 'isTrav'
	let letters: any = null
	let timer: any = null

	function arrayRotate(arr: any, reverse: boolean) {
		if (reverse) arr.unshift(arr.pop());
		else arr.push(arr.shift());
		return arr;
	}

	function go() {
		// console.log('go')
		timer = setInterval(() => {
			let rotate: string[] = letters || name.split('')
			letters = arrayRotate(rotate, true)
			name = letters.join('')
		}, 500)
	}

	function stop() {
		// console.log('stop')
		clearInterval(timer)
	}
</script>

<header on:mouseenter={() => go()} on:mouseleave={() => stop()}>
  <nav class="top">
		<div class="nav-wrapper">
			<a href="//istrav.communityfolder.com" class="btn right" style="margin: 1em;">community</a>
      <a href="/" class="brand-logo center">{name}</a>
			<ul id="nav-mobile" class="right hide-on-med-and-down">

				<li class:active={$page.url.pathname.startsWith('/client-area')}>
					<a sveltekit:prefetch href="/client-area">Clients</a>
				</li>
				<li class:active={$page.url.pathname === '/network-ai'}>
					<a sveltekit:prefetch href="/network-ai">Network AI</a>
				</li>
				<li class:active={$page.url.pathname === '/about'}>
					<a sveltekit:prefetch href="/about">About</a>
				</li>
			</ul>
			<ul id="nav-mobile" class="left hide-on-med-and-down">
				<li class:active={$page.url.pathname === '/production'}>
					<a sveltekit:prefetch href="/production">Production</a>
				</li>
				<li class:active={$page.url.pathname === '/solutions'}>
					<a sveltekit:prefetch href="/solutions">Solutions</a>
				</li>
				<li class:active={$page.url.pathname === '/apps'}>
					<a sveltekit:prefetch href="/apps">Apps</a>
				</li>
				<li class:active={$page.url.pathname.startsWith('/platforms')}>
					<a sveltekit:prefetch href="/platforms">Platforms</a>
				</li>
				<li class:active={$page.url.pathname === '/projects'}>
					<a sveltekit:prefetch href="/projects">Projects</a>
				</li>
			</ul>
		<div>
  </nav>
</header>

<style>
	header {
		height: 4.25em;
	}
  .top {
    z-index: 1000;
    position: fixed;
    right: 0;
    left: 0;
    margin: 0;
    padding: 0;
  }
</style>