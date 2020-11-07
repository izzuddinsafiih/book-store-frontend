<script context='module'>
    export async function preload({ params }) {
        const { bookId } = params;

        const res = await this.fetch(
            `https://bookstoresizzuddin.herokuapp.com/books/${bookId}`
        );

        const book = await res.json();

        return { book }
    }
</script>
<script>
    export let book;

    let newTitle = book.title;
    let newPrice = book.price;
    let newDesc = book.description;
    let newNOP = book.number_of_pages;

    async function handleUpdateBook() {
        console.log("Updating book...");

        const data = {  
            id: book.id,
            title: newTitle,
            price: newPrice,
            description: newDesc,
            number_of_pages: newNOP,
        };

        const res = await fetch(
                `https://bookstoresizzuddin.herokuapp.com/books/${book.id}`,
                {
                    method: "PUT",
                    headers: {
                        "Content-Type": "application/json",
                    },
                    body: JSON.stringify(data)
                }
        );

        const resData = await res.json();

        console.log(resData);

        const { host } = window.location;
        console.log(host);
        window.location.href = `http://${host}/book/${book.id}`;
    }

    async function handleDeleteBook() {
        const res = await fetch(
                `https://bookstoresizzuddin.herokuapp.com/books/${book.id}`,
                {
                    method: "DELETE",
                }
        );        

        const { host } = window.location;
        console.log(host);
        window.location.href = `http://${host}`;
    }        
</script>

<style>
    main {
        background-color: burlywood;
        padding: 24px;
    }

    .field-item {
        display: flex;
        align-items: center;
        padding: 16px;
        background-color: rgb(255, 247, 236);
        border-radius: 10px;
        margin-bottom: 10px;
    }

    .field-item h4 {
        margin: 0;
        width: 100px;  
    }

    .field-item input {
        height: 100%;
    }
</style>

<svelte:head>
    <title>{book.title} | Book Store</title>
</svelte:head>

<main>
    <div class="field-item">
        <h4>Title</h4>
        <input type="text" bind:value={newTitle} />
    </div>

    <div class="field-item">
        <h4>price (RM)</h4>
        <input type="text" bind:value={newPrice} />
    </div>

    <div class="field-item">
        <h4>Description</h4>
        <input type="text" bind:value={newDesc} />
    </div>

    <div class="field-item">
        <h4>Number of Pages</h4>
        <input type="text" bind:value={newNOP} />
    </div>

    <a href="book/{book.id}">
        <button>Back</button>
    </a>
    <button on:click={handleUpdateBook}>Update</button>
    <button on:click={handleDeleteBook}>Remove</button>
</main>

