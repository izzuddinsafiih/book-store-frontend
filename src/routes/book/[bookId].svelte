<script context='module'>
    export async function preload({ params }) {
        const { bookId } = params;

        const res = await this.fetch(`https://bookstoresizzuddin.herokuapp.com/books/${bookId}`);

        const book = await res.json();

        return { book }
    }
</script>
<script>
    export let book;
</script>

<style>
    main {
        background-color: burlywood;
        padding: 24px;
    }

    .book-title {
        font-weight: 700;
        font-size: 48px;
    }

    .book-price {
        color: rgb(97, 56, 3);
        font-weight: 500;
    }

    .desc-title {
        margin-top: 30px;
        color: rgb(0, 2, 2);
        font-weight: 700;
    }
</style>

<svelte:head>
    <title>{book.title} | Book Store</title>
</svelte:head>

<main>
    <h1 class='book-title'>{book.title}</h1>

    <h2 class="book-price">RM {book.price}</h2>

    <h3 class="desc-title">Description</h3>

    <p>{book.description}</p>

    <!-- <h3 class="desc-title">Owner</h3>

    <p>{book.owner}</p> -->

    <button>Buy Now</button>
    <a href="book/edit/{book.id}">
        <button>Edit</button>
    </a>
</main>
