<script>
    import Modal from './modal.svelte';
    import {goto} from '$app/navigation';
    let modal;
</script>

<div class="container">
    <h1>contact</h1>
    <button on:click={() => goto('/')}  >go back</button>
    <textarea ></textarea>
    <button on:click={() => modal.show()}  >show modal</button>
    <Modal bind:this={modal}>
        <h1>email me</h1>
        <p>hello world!</p>
    </Modal>
</div>

<style>
    .container{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    textarea{
        width: 100%;
        height: 80vh;
        background-color: var(--main-maroon);
    }
</style>