<script>
    let shown = false;
    export function show(){
        shown = true;
    }
    export function hide(){
        shown = false;
    }
</script>

<svelte:window on:keydown={(e) => {
    if(e.keyCode == 27){
        hide();
    }
}}/>
{#if shown}
<div class="modal-wrapper">
    <div class="modal">
        
        
        <slot></slot>
    </div>
</div>

{/if}

<style>
    .modal-wrapper{
        background-color: rgb(0,0,0);
        background-color: rgba(0,0,0,0.6);
        position: fixed;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
    }
    .modal{
        background-color: var(--main-white);
        border-radius: .75rem;
        width: 80vw;
        padding: 1rem;
        margin: 15% auto;

    }
    
</style>