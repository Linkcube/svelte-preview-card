<script>
    import { createEventDispatcher } from 'svelte';
    export let background_source = false;
    export let primary_text = false;
    export let sub_text = false;
    export let alt_text = "preview_image";
    export let background_color = "white";
    export let active_color = "lightgrey";
    export let focus_color = background_color;
    export let primary_text_color = "black";
    export let sub_text_color = "grey";
    export let disabled = false;

    const dispatch = createEventDispatcher();

    let max_height = 180;
    if (!primary_text) max_height += 20;
    if (!sub_text) max_height += 20;
    max_height = `${max_height}px`;
    if (disabled) active_color = 0;
</script>

<style>
    .card {
        height: 250px;
        width: 220px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin: 10px;
        transition-duration: 500ms;
        box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.1);
        cursor: pointer;
        border: none;
        outline:none;
        background: var(--background_color);
        line-height: 1em;
        padding: 0px;
        
    }

    .card:hover {
        transition-duration: 500ms;
        box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.4);
    }

    .card:focus {
        background: var(--focus_color);
    }

    .card:active {
        background: var(--active_color)
    }

    .card::-moz-focus-inner {
        border: 0;
    }

    img {
        display: flex;
        max-width: 180px;
        max-height: var(--height);
        transition-duration: 500ms;
        margin-left: auto;
        margin-right: auto;
        opacity: .9;
        outline: 1px solid transparent;
    }

    .card:hover img {
        opacity: 1;
        transition-duration: 500ms;
        outline: 1px solid transparent;
    }

    .primary-text {
        text-align: center;
        color: var(--primary-color);
        font-size: 20px;
    }

    .sub-text {
        text-align: center;
        color: var(--primary-color);
    }

    .footer {
        margin: auto;
        width: 220px;
        line-height: 1.5em;
    }

    .hover {
        margin-top: auto;
        margin-bottom: auto;
        width: 220px;
    }

</style>

<button class="card" style="--background_color:{background_color};--active_color:{active_color};--focus_color:{focus_color}" on:click={() => dispatch('open')} {disabled}>
    {#if background_source !== false}
        <div class="hover">
            <img src={background_source} alt={alt_text} style="--height:{max_height}">
        </div>
    {/if}
    <div class="footer">
        {#if primary_text}
            <div class="primary-text" style="--primary-color:{primary_text_color}">{primary_text}</div>
        {/if}
        {#if sub_text}
            <div class="sub-text" style="--primary-color:{sub_text_color}">{sub_text}</div>
        {/if}
    </div>
</button>
