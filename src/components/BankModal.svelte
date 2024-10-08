<script lang="ts">
    export let bankData;
    export let showModal: Boolean;

    let bankDialog: HTMLDialogElement;

    $: if (bankDialog && showModal && bankData) {
        document.body.style.overflow = 'hidden';
        bankDialog.showModal();
    }

    function closeModal() {
        showModal = false;
        document.body.style.overflow = '';
    }

    function copyAccount(account: string) {
        window.navigator.clipboard.writeText(account).then(() => {
            alert(`계좌번호가 복사 되었습니다.\n${account}`);
        });
    }
</script>

<dialog class="modal-wrapper" bind:this={bankDialog} on:close={closeModal}>
    <button class="modal-bg" on:click={() => bankDialog.close()}></button>
    <div class="modal-window">
        <header class="modal-header">
            <h2>{bankData.type}측 계좌번호</h2>
        </header>
        <ul class="bank-modal-contents">
            {#if bankData.type}
                <li>
                    <div>
                        <div>{bankData.father.bank}</div>
                        <div>예금주: {bankData.father.name}</div>
                    </div>
                    <div>
                        <p>{bankData.father.account}</p>
                        <button type="button" on:click={() => copyAccount(bankData.father.account)}>
                            복사
                        </button>
                    </div>
                </li>
                <li>
                    <div>
                        <div>{bankData.mother.bank}</div>
                        <div>예금주: {bankData.mother.name}</div>
                    </div>
                    <div>
                        <p>{bankData.mother.account}</p>
                        <button type="button" on:click={() => copyAccount(bankData.mother.account)}>
                            복사
                        </button>
                    </div>
                </li>
                <li>
                    <div>
                        <div>{bankData.bank}</div>
                        <div>
                            예금주: {bankData.name}
                        </div>
                    </div>
                    <div>
                        <p>{bankData.account}</p>
                        <button type="button" on:click={() => copyAccount(bankData.account)}>
                            복사
                        </button>
                        <a class="kakao-pay" href={bankData.kakaoPay}>
                            <img src="./img/kakao-pay-icon.png" alt="카카오페이로 송금하기" />
                        </a>
                    </div>
                </li>
            {/if}
        </ul>
    </div>
</dialog>

<style>
    .bank-modal-contents {
        padding: 1.2rem 1.5rem 0.5rem;
    }
    .bank-modal-contents > li {
        width: 100%;
        margin-bottom: 1.6rem;
        font-size: 1.2rem;
    }
    .bank-modal-contents > li > div {
        display: flex;
        justify-content: space-between;
        margin: 0.3rem 0;
    }
    .bank-modal-contents > li > div > p {
        flex: 1;
        padding: 1rem;
        border: 1px solid #999;
        border-right-width: 0;
        border-top-left-radius: 0.3rem;
        border-bottom-left-radius: 0.3rem;
    }
    .bank-modal-contents > li > div > button {
        padding: 0.6rem 1rem;
        border: 1px solid #9c0d0daf;
        background-color: #9c0d0daf;
        color: #fff;
        border-top-right-radius: 0.3rem;
        border-bottom-right-radius: 0.3rem;
    }
    .bank-modal-contents > li:last-of-type > div > button {
        margin-right: 0.5rem;
    }
    .kakao-pay {
        display: flex;
        padding: 0.4rem;
        background-color: #fae100;
        border-radius: 0.3rem;
    }
    .kakao-pay img {
        width: 3.6rem;
        object-fit: contain;
    }
</style>
