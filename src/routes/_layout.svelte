<script>
    import UserObserver from '../components/UserObserver.svelte';
    import Login from '../components/Login.svelte';
    import TopAppBar from '../components/TopAppBar.svelte';
</script>

<style>
	main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
    #top-bar {
        grid-area: topbar;
    }
    #content {
        grid-area: content;
    }
    #layout-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-auto-rows: minmax(100px, auto);
        grid-template-areas: 
        "topbar  topbar  topbar"
        "content content content"
    }
</style>
<UserObserver />
<div id="layout-grid">
    <div id="top-bar">
        <TopAppBar />
    </div>
    <main id="content">
	    <slot></slot>
    </main>
</div>