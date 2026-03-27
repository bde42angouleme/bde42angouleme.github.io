<script lang="ts">
	let { children } = $props();

	const sendPointerExpand = () => {
		document.dispatchEvent(new CustomEvent('pointerExpand'));
	};

	const sendPointerCollapse = () => {
		document.dispatchEvent(new CustomEvent('pointerCollapse'));
	}
</script>

<div onmouseenter={sendPointerExpand} onmouseleave={sendPointerCollapse} role="link" tabindex="-1" style="display: inline-block;">
	{@render children()}
</div>