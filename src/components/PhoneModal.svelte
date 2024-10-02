<script lang="ts">
    export let data;
    export let showModal:Boolean;

    let dialog:HTMLDialogElement;

    $: if (dialog && showModal && data) {
        document.body.style.overflow = 'hidden'
        dialog.showModal();
    }

    function closeModal() {
        showModal = false;
        document.body.style.overflow = '';
    }
</script>

<dialog class="modal-wrapper" bind:this={dialog} on:close={closeModal}>
    <button class="modal-bg" on:click={() => dialog.close()}></button>
    <div class="modal-window">
        <header class="modal-header">
            <h2>연락하기</h2>
        </header>
        <ul class="modal-contents">
            {#if data.type}
            <li>
                <div>{data.type}</div>
                <div>{data.name}</div>
                <a href={`tel:${data.phone}`}><img src="/public/img/phone.png" alt="전화하기" /></a>
                <a href={`sms:${data.phone}`}><img src="/public/img/sms.png" alt="문자하기" /></a>
            </li>
            <li>
                <div>{data.type} 아버지</div>
                <div>{data.father.name}</div>
                <a href={`tel:${data.father.phone}`}><img src="/public/img/phone.png" alt="전화하기" /></a>
                <a href={`sms:${data.father.phone}`}><img src="/public/img/sms.png" alt="문자하기" /></a>
            </li>
            <li>
                <div>{data.type} 어머니</div>
                <div>{data.mother.name}</div>
                <a href={`tel:${data.mother.phone}`}><img src="/public/img/phone.png" alt="전화하기" /></a>
                <a href={`sms:${data.mother.phone}`}><img src="/public/img/sms.png" alt="문자하기" /></a>
            </li>
            {/if}
        </ul>
    </div>
</dialog>

<style>
    .modal-wrapper {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100dvh;
        background-color: #00000070;
    }
    .modal-bg {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }
    .modal-window {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 80%;
        background: #fff;
        border-radius: 10px;
        z-index: 2;
    }
    .modal-header {
        padding: 0.5rem 0;
        background-color: #ecdddd;
        text-align: center;
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
    }
    .modal-header > h2 {
        font-size: 1.2rem;
        color: #333;
    }
    .modal-contents {
        padding: 1.5rem;
    }
    .modal-contents > li {
        display: flex;
        align-items: center;
        justify-content: space-around;
        width: 100%;
        margin: 0.7rem 0;
    }
    .modal-contents > li > div:first-of-type {
        width: 25%;
        text-align: left;
    }
    .modal-contents > li > div:nth-of-type(2) {
        width: 35%;
    }
    .modal-contents a img {
        width: 1.7rem;
    }
</style>