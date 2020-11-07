<script>
    export let id;
    export let title;
    export let price;
</script>


<style>
    a {
        text-decoration: none;
    }

    main{
        display: flex;
        flex-flow: column nowrap;
        justify-content: center;
        align-items: center;
        width: 250px;
        height: 150px;
        background-color: azure;
        margin: 5px;
        padding: 10px;
    }

    h1 {
        font-weight: 700;
        font-size: 20px;
        text-align: center;
    }

    h2 {

    }    
</style>

<a href="book/{id}">
    <main>
        <h1>{title}</h1>
        <h2>RM {price.toFixed(2)}</h2>
    </main>
</a>
