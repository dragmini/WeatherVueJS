<template>
    <div class="options__modal">
        <div class="header-options">
            <p>Andrey Belyaev</p>
            <button class="exit_account"><i class="bi bi-box-arrow-right"></i></button>
        </div>
        <div class="line"></div>
        <div class="options-menu">
            <button class="btn-options">Редактировать</button>
            <button class="btn-options">Виджеты</button>
            <button class="btn-options">Связаться с автором</button>
        </div>
    </div>
</template>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Alegreya+Sans:wght@500&display=swap');

    .options__modal {
        /* display: none; */
        position: absolute;
        background: #1f1f1f;
        color: #fff;
        width: 200px;
        height: 200px;
        border: 1px #000 solid;
        right: 10px;
        top: 100px;
        border-radius: 20px;
    }
    .line {
        height: 1px;
        background: #929CDE;
    }
    .exit_account {
        background: transparent;
        color: #fff;
        border: none;
        font-size: 22px;
    }
    .header-options {
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
    }
    .header-options p {
        font-family: Alegreya Sans;
        font-style: normal;
        font-weight: bold;
        font-size: 18px;
    }
    .btn-options {
        font-family: Alegreya Sans;
        font-style: normal;
        font-weight: normal;
        background: #fff;
        color: #000;
        font-size: 16px;
        border: none;
        width: 80%;
        margin-top: 10px;
        padding-top: 5px;
        padding-bottom: 5px;
        border-radius: 10px;
    }
    .options-menu {
        display: flex;
        flex-direction: column;
        align-items: center;
        /* justify-content: center; */
        margin-top: 7px;
    }
</style>