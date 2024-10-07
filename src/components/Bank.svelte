<script lang="ts">
    import { groom, bride } from '../contents/contact';
    import BankModal from './BankModal.svelte';

    let data = {};
    let showModal = false;

    function handleBankModal(type: 'groom' | 'bride') {
        if (type === 'groom') {
            data = groom;
        } else data = bride;

        showModal = true;
    }
</script>

<div class="bank-area">
    <img src="./public/img/bell.png" alt="크리스마스 종" />
    <h2>마음 전하실 곳</h2>
    <p>참석이 어려우신 분들을 위해 계좌번호를 기재했습니다.</p>
    <p>축하해 주시는 따뜻한 마음에 감사드립니다.</p>

    <div class="bank-account-buttons">
        <button type="button" on:click={() => handleBankModal('groom')}>신랑측 계좌번호</button>
        <button type="button" on:click={() => handleBankModal('bride')}>신부측 계좌번호</button>
    </div>
</div>
<BankModal bind:showModal bankData={data} />

<style>
    .bank-area {
        padding: 1rem 1.5rem;
    }
    .bank-area > h2 {
        padding-bottom: 0.8rem;
        font-size: 1.3rem;
        color: #555;
    }
    .bank-area > img {
        width: 15%;
        margin: 0 auto 5rem;
    }
    .bank-area > p {
        color: #777;
    }
    .bank-account-buttons > button {
        width: 100%;
        padding: 1.2rem 0;
        margin-top: 0.8rem;
        background-color: #077d0e;
        color: #fff;
        border-radius: 1rem;
    }
    .bank-account-buttons > button:nth-of-type(2) {
        background-color: #9c0d0d;
    }
</style>
