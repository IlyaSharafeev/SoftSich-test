<div class="page-popup">
    <div class="background-header"></div>
    <button class="open-modal-button" on:click={() => showModal = true}>Открыть окно</button>

    {#if showModal}
        <div class="modal">
            <div class="overlay-store"></div>
            <div class="modal-content">
                <div class="modal-content__header">
                    <div class="balance"></div>
                </div>
                <div class="modal-content__body">
                    <div class="modal-content__body-header">
                        <div class="modal-content__button-close" on:click={() => showModal = false}></div>
                        <div class="modal-content__coins"></div>
                        <div class="modal-content__safe"></div>
                        <div class="modal-content__stars-left"></div>
                        <div class="modal-content__stars-right"></div>
                    </div>
                    <div class="modal-content__body-content">
                        <div class="modal-content__body-content-background-name"></div>
                        <div class="modal-content__body-content-timer-wrapper">
                            <div class="modal-content__body-content-timer">
                                <p>{timeLeft}</p>
                            </div>
                        </div>
                        <div class="modal-content__body-content-description">
                            <div>Spin slot MEGALOAD2000</div>
                            <div>at Least 10 times with at </div>
                            <div>least $10 Bet amount</div>
                            <div>least 10 Times with</div>
                        </div>
                        <div class="modal-content__body-content-price"></div>
                        <div class="modal-content__body-content-button">
                            <div class="modal-content__body-content-button-reflex"></div>
                            <div class="modal-content__body-content-button-text"></div>
                        </div>
                    </div>

                </div>
                <div class="overlay-modal"></div>
            </div>
        </div>
    {/if}
    <div class="background-footer"></div>
</div>

<script>
    import { onMount } from 'svelte';

    let showModal = true;
    let timeLeft = '';

    function updateTime() {
        const now = new Date();
        const midnight = new Date();
        midnight.setHours(24, 0, 0, 0);
        const diff = midnight - now;

        const days = Math.floor(diff / (1000 * 60 * 60 * 24));
        const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((diff % (1000 * 60)) / 1000);

        timeLeft = `${days}d ${hours}h ${minutes}m ${seconds}s`;
    }

    onMount(() => {
        updateTime();
        const interval = setInterval(updateTime, 1000);
        return () => clearInterval(interval);
    });
</script>

<style>
    @import "../styles/_reset/reset.scss";
    
    .background-footer {
        background-image: url('/assets/background-footer.png');
        background-size: cover;
        background-position: center;
        width: 100vw;
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        bottom: 0;
        height: 348px;
    }
    .background-header {
        background-image: url('/assets/background-header.png');
        background-size: contain;
        background-position: center;
        width: 100vw;
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        height: 290px;
    }
    .open-modal-button {
        padding: 10px 20px;
        font-size: 16px;
        cursor: pointer;
        z-index: 1;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    .modal {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(12, 10, 22, 0.83);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 2;
        
        .overlay-modal {
            position: absolute;
            background-image: url('/assets/overlay-modal.png');
            background-size: contain;
            background-position: center;
            background-repeat: no-repeat;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 1076px;
            height: 1076px;
            z-index: 3;
        }
        
        .overlay-store {
            position: absolute;
            background-image: url('/assets/background-store.png');
            background-size: contain;
            background-position: center;
            background-repeat: no-repeat;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 964px;
            height: 1340px;
            z-index: 2;
        }
        
        .modal-content {
            background: linear-gradient(0.39deg, rgba(38, 18, 68, 0.95) 0.34%, rgba(20, 14, 35, 0.95) 99.66%);
            padding: 20px;
            border-radius: 25px;
            text-align: center;
            position: relative;
            height: 1620px;
            width: 100%;
            z-index: 3;
            box-shadow: 0px 12px 6px 0px #00000080;
            box-shadow: 2.4px 2.4px 0px 0px #FFFFFF26 inset;
            box-shadow: -2.4px -2.4px 0px 0px #99F9F926 inset;


            .modal-content__header {
                position: absolute;
                top: 23px;
                left: 18px;
                
                .balance {
                    background-image: url('/assets/balance.png');
                    background-repeat: no-repeat;
                    background-size: contain;
                    width: 271px;
                    height: 90px;
                    position: relative;
                }
            }

            .modal-content__body {
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                z-index: 5;
                
                .modal-content__body-header {
                    background-image: url('/assets/header-body.png');
                    width: 675px;
                    height: 361px;
                    position: relative;
                    
                    .modal-content__button-close {
                        background-image: url('/assets/close-button.png');
                        background-repeat: no-repeat;
                        background-size: contain;
                        width: 111px;
                        height: 111px;
                        position: absolute;
                        top: 10px;
                        right: -73px;
                        cursor: pointer;
                    }
                    
                    .modal-content__coins {
                         background-image: url('/assets/coins.png');
                         background-repeat: no-repeat;
                         background-size: contain;
                         width: 612px;
                         height: 140px;
                         position: absolute;
                         bottom: 100px;
                         left: 30px;
                         cursor: pointer;
                    }
                    
                    .modal-content__safe {
                        background-image: url('/assets/safe.png');
                        background-repeat: no-repeat;
                        background-size: contain;
                        width: 475px;
                        height: 475px;
                        position: absolute;
                        bottom: 15px;
                        left: 95px;
                        cursor: pointer;
                        z-index: 3;
                    }

                    .modal-content__stars-left {
                        position: absolute;
                        top: -137px;
                        left: 130px;
                        width: 154px;
                        height: 154px;
                        background-image: url("/assets/stars-left.png");
                        z-index: -1;
                    }

                    .modal-content__stars-right {
                        position: absolute;
                        top: -79px;
                        right: 101px;
                        width: 165px;
                        height: 217px;
                        background-image: url("/assets/stars-right.png");
                        z-index: -1;
                        transform: translateZ(-1px);
                    }
                }
                .modal-content__body-content {
                    position: relative;
                    background-image: url('/assets/body-content.png');
                    width: 675px;
                    height: 768px;
                    display: flex;
                    justify-content: center;
                    flex-direction: column;
                    align-items: center;
                    
                    .modal-content__body-content-background-name {
                        position: absolute;
                        top: -100px;
                        right: -65px;
                        background-image: url('/assets/background-name.png');
                        width: 802px;
                        height: 160px;
                        z-index: 5;
                    }
                    
                    .modal-content__body-content-timer-wrapper {
                        box-shadow: 0px 2.79px 0px 0px #EFF7FD;
                        box-shadow: 0px 6.98px 6.98px 0px #B7C3CB inset;
                        border-radius: 20px;
                        background: #e0ebee;
                        width: 585px;
                        padding: 16px;

                        .modal-content__body-content-timer {
                            font-family: Fira Sans;
                            font-weight: 600;
                            font-size: 39px;
                            text-align: center;
                            color: #828896;
                        }
                    }
                    
                    .modal-content__body-content-description {
                        margin-top: 46px;
                        font-family: Fira Sans;
                        font-weight: 600;
                        font-size: 42px;
                        line-height: 50.4px;
                        letter-spacing: 0%;
                        text-align: center;
                        color: #828896;
                        height: 224px;
                    }
                    
                    .modal-content__body-content-price {
                        background-image: url("/assets/price.png");
                        background-repeat: no-repeat;
                        background-position: center;
                        width: 300px;
                        height: 75px;
                        margin-bottom: 14px;
                        margin-top: 60px;
                    }
                    
                    .modal-content__body-content-button {
                        position: relative;
                        display: flex;
                        justify-content: center;
                        width: 585px;
                        height: 126px;
                        border-radius: 30px;
                        background: linear-gradient(180deg, #28D323 1%, #16BC34 52.5%, #31F02D 100%);
                        
                        .modal-content__body-content-button-reflex {
                            position: absolute;
                            top: 0;
                            margin: 10.5px;
                            border-radius: 24px;
                            width: 564px;
                            height: 63px;
                            background: linear-gradient(180deg, #9CF99A 0%, #46F352 54%, #40E25F 100%);
                        }
                        
                        .modal-content__body-content-button-text {
                            background-image: url('/assets/text-buy.svg');
                            background-repeat: no-repeat;
                            background-size: contain;
                            width: 88px;
                            height: 61px;
                            margin: 45px 29px;
                            z-index: 2;
                        }
                    }
                }
            }
        }
    }
    /*.close {*/
    /*    position: absolute;*/
    /*    top: 10px;*/
    /*    right: 10px;*/
    /*    border: none;*/
    /*    background: none;*/
    /*    font-size: 20px;*/
    /*    cursor: pointer;*/
    /*}*/
    /*.buy {*/
    /*    padding: 10px 20px;*/
    /*    font-size: 16px;*/
    /*    background: gray;*/
    /*    border: none;*/
    /*    cursor: not-allowed;*/
    /*}*/
</style>