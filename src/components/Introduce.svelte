<script lang="ts">
    import PhoneModal from './PhoneModal.svelte';
    import { groom, bride } from '../contents/contact';

    let showModal = false;
    let data = {};

    function showPhoneModal(type: 'groom' | 'bride') {
        if (type === 'groom') {
            data = groom;
        } else data = bride;

        showModal = true;
    }
</script>

<div class="introduce-area">
    <div class="poem-wrapper">
        <img src="./img/line.png" alt="" />
        물들었습니다 서로에게. <br />
        시나브로, 조<span>용</span>히, 진하게.<br />
        모자름에 연<span>연</span>하지 않았고,<br />
        넘치는 것은 나누었습니다.<br />
        그러다 <span>보</span>니, 오늘이 왔네요.<br />
        앞으로 펼쳐질 저희의 <span>미</span>래를<br />
        따뜻한 시선으로 지켜봐 주세요.<br />

        <img src="./img/line2.png" alt="" />
    </div>

    <ul class="groom-and-bride">
        <li>
            <img src="./img/groom.png" alt="신랑 김용연" />
            <div>
                <p>김원종 <span></span> 김남희의 <br />첫째 아들 <b>김용연</b></p>
                <button type="button" on:click={() => showPhoneModal('groom')}>연락하기</button>
            </div>
        </li>
        <li>
            <img src="./img/bride.png" alt="신부 성보미" />
            <div>
                <p>성임식 <span></span> 박병인의 <br />셋째 딸 <b>성보미</b></p>
                <button type="button" on:click={() => showPhoneModal('bride')}>연락하기</button>
            </div>
        </li>
    </ul>
    <PhoneModal bind:showModal phoneData={data} />
</div>

<style>
    .introduce-area {
        padding: 1.5rem;
        text-align: center;
    }
    .poem-wrapper {
        padding: 1rem 0;
        color: #666;
        font-size: 1rem;
        line-height: 2.5rem;
    }
    .poem-wrapper > img {
        width: 35%;
        max-width: 9rem;
        margin: 1rem auto;
    }
    .poem-wrapper > img:nth-of-type(2) {
        width: 50%;
        max-width: 100%;
        margin-top: 1.8rem;
    }
    .poem-wrapper > span {
        font-size: 1.4rem;
        font-weight: bold;
    }
    span:nth-of-type(1),
    span:nth-of-type(3) {
        color: #077d0e;
    }
    span:nth-of-type(2),
    span:nth-of-type(4) {
        color: #9c0d0d;
    }

    .groom-and-bride {
        width: 100%;
        padding-top: 2rem;
    }
    .groom-and-bride li {
        display: flex;
        align-items: center;
        gap: 3rem;
        font-size: 0.9rem;
        color: #333;
    }
    .groom-and-bride img {
        width: 50%;
    }
    .groom-and-bride li:nth-of-type(2) {
        flex-direction: row-reverse;
    }
    .groom-and-bride li span {
        display: inline-block;
        position: relative;
        width: 3px;
        height: 0.7rem;
    }
    .groom-and-bride li span::after {
        content: '';
        width: 3px;
        height: 3px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: #666;
        border-radius: 100%;
    }
    .groom-and-bride li button {
        width: 100%;
        padding: 0.5rem 2rem 0.4rem;
        margin-top: 0.5rem;
        border: 1px solid #ccc;
        border-radius: 20px;
        color: #666;
    }
</style>
