<script>
    let sectionA = ["Lorem", "Ipsum", "Dolor", "Sit amet", "Consectetur"];
    let sectionB = ["Adipiscing", "Elit", "Do eiusmod", "Incididunt", "Ut labore"];
    let sectionC = ["Magna", "Aliqua", "Enim", "Minim", "Veniam"];
</script>

<footer>
    <div>
        <ul>
            {#each sectionA as itemA}
                <li>{itemA}</li>
            {/each}
        </ul>
    </div>
     <div>
        <ul>
            {#each sectionB as itemB}
                <li>{itemB}</li>
            {/each}
        </ul>
    </div>
     <div>
        <ul>
            {#each sectionC as itemC}
                <li>{itemC}</li>
            {/each}
        </ul>
    </div>
</footer>

<style>
    footer {
        display: flex;
        justify-content: space-evenly;
        width: 100vw;
        background-color: #63D2FF;
    }
    ul {
        list-style-type: none;
    }
    li {
        color: #F7F9F9;
        line-height: 2em;
        cursor: pointer;
    }
    li:hover {
        color: #2081C3;
    }
    div {
        padding: 5px;
        margin: 3em auto;
    }

    @media only screen and (max-width: 470px){
        footer {
            flex-direction: column;
        }
        div {
            margin: 0.75em auto;
        }
    }
</style>