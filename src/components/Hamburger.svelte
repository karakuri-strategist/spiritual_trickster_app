<script>
    let className;
    export {className as class};
</script>

<button on:click class={`${className} hamburger`} aria-label="Open the menu">
    <span class="line" aria-hidden="true"></span>
    <span class="line" aria-hidden="true"></span>
    <span class="line last" aria-hidden="true"></span>
</button>

<style>
    .hamburger {
        background: none;
        color: inherit;
        border: none;
        padding: 0;
        font: inherit;
        cursor: pointer;
        outline: inherit;
        justify-content: center;
        flex-direction: column;
        display: flex;
        align-items: center;
        cursor: pointer;
    }

    .hamburger .line.last {
        margin-bottom: 0;
    }

    .hamburger .line {
        display: block;
        width: 30px;
        height: 3px;
        margin-bottom: 7px;
        background-color: white;
    }
</style>
