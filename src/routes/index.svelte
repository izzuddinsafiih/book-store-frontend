<script context="module">
	export async function preload({ page, session }) {
		const res = await this.fetch(
			"https://bookstoresizzuddin.herokuapp.com/books"
		);
		const books = await res.json();

		return { books };
	}
</script>

<script>
	import BookCard from "../components/BookCard.svelte";

	export let books;
</script>

<style>
	.container {
		display: flex;
		flex-flow: row wrap;
	}
</style>

<svelte:head>
	<title>Book Store</title>
</svelte:head>

<h1>Book Store</h1>

{#if books}
	<div class="container">
		{#each  books as book}
			<BookCard id={book.id} title={book.title} price={book.price} />
		{/each}
	</div>
{/if}