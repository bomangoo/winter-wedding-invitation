<script lang="ts">
    export let phoneData;
    export let showModal: Boolean;

    let dialog: HTMLDialogElement;

    $: if (dialog && showModal && phoneData) {
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
            <h2>{phoneData.type}측 연락하기</h2>
        </header>
        <ul class="modal-contents">
            {#if phoneData.type}
                <li>
                    <div>{phoneData.type}</div>
                    <div>{phoneData.name}</div>
                    <a href={`tel:${phoneData.phone}`}
                        ><img src="./public/img/phone.png" alt="전화하기" /></a
                    >
                    <a href={`sms:${phoneData.phone}`}
                        ><img src="./public/img/sms.png" alt="문자하기" /></a
                    >
                </li>
                <li>
                    <div>{phoneData.type} 아버지</div>
                    <div>{phoneData.father.name}</div>
                    <a href={`tel:${phoneData.father.phone}`}
                        ><img src="./public/img/phone.png" alt="전화하기" /></a
                    >
                    <a href={`sms:${phoneData.father.phone}`}
                        ><img src="./public/img/sms.png" alt="문자하기" /></a
                    >
                </li>
                <li>
                    <div>{phoneData.type} 어머니</div>
                    <div>{phoneData.mother.name}</div>
                    <a href={`tel:${phoneData.mother.phone}`}
                        ><img src="./public/img/phone.png" alt="전화하기" /></a
                    >
                    <a href={`sms:${phoneData.mother.phone}`}
                        ><img src="./public/img/sms.png" alt="문자하기" /></a
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
