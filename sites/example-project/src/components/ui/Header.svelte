<script>
    import BreadCrumbs from './BreadCrumbs.svelte';
    import PrintButton from './PrintButton.svelte';
    export let menu;
    export let folderList;
</script>

<header>
    <div class="breadcrumb-container">
        <BreadCrumbs {menu} {folderList}/>
        <PrintButton/>
    </div>
</header>

<style>
header {
    grid-area: header;
    position: sticky;
    z-index: 2;
    top: 0;
    height: var(--header-height);
    background-color: rgba(255, 255, 255, 0.73);
    -webkit-backdrop-filter: blur(20px) saturate(1.8);
    backdrop-filter: blur(20px) saturate(1.8);
    width: 100%;
}

div.breadcrumb-container {
	height: var(--header-height);
	box-sizing: border-box;
	display: flex;
	justify-items: right;
	align-items: center; 
}

@media print {
    header {
      display: none;
    }
}

</style>