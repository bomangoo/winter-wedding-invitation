<script lang="ts">
    export let data;
    export let showModal: Boolean;

    let dialog: HTMLDialogElement;

    $: if (dialog && showModal && data) {
        document.body.style.overflow = 'hidden';
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
            <h2>{data.type}측 연락하기</h2>
        </header>
        <ul class="modal-contents">
            {#if data.type}
                <li>
                    <div>{data.type}</div>
                    <div>{data.name}</div>
                    <a href={`tel:${data.phone}`}
                        ><img src="/public/img/phone.png" alt="전화하기" /></a
                    >
                    <a href={`sms:${data.phone}`}
                        ><img src="/public/img/sms.png" alt="문자하기" /></a
                    >
                </li>
                <li>
                    <div>{data.type} 아버지</div>
                    <div>{data.father.name}</div>
                    <a href={`tel:${data.father.phone}`}
                        ><img src="/public/img/phone.png" alt="전화하기" /></a
                    >
                    <a href={`sms:${data.father.phone}`}
                        ><img src="/public/img/sms.png" alt="문자하기" /></a
                    >
                </li>
                <li>
                    <div>{data.type} 어머니</div>
                    <div>{data.mother.name}</div>
                    <a href={`tel:${data.mother.phone}`}
                        ><img src="/public/img/phone.png" alt="전화하기" /></a
                    >
                    <a href={`sms:${data.mother.phone}`}
                        ><img src="/public/img/sms.png" alt="문자하기" /></a
                    >
                </li>
            {/if}
        </ul>
    </div>
</dialog>

<style>
    .modal-contents {
        padding: 1.2rem 1.5rem;
    }
    .modal-contents > li {
        display: flex;
        justify-content: space-around;
        width: 100%;
        margin: 0.8rem 0;
        font-size: 1.2rem;
    }
    .modal-contents > li > div:first-of-type {
        width: 30%;
        text-align: left;
        color: #9c7979;
    }
    .modal-contents > li > div:nth-of-type(2) {
        width: 33%;
        color: #333;
    }
    .modal-contents > li a img {
        width: 1.5rem;
    }
    .modal-contents > li a:nth-of-type(2n) img {
        width: 1.7rem;
    }
</style>
