<script>
export default {
    name: 'DataBinding',
    data() {
        return {
            backgroundBox: '',
            textColor: '',
            showTexto: false,
            borderBox: '0',
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="selectores">
            <label for="backgroundBoxInput">Color de fondo: </label>
            <input id="backgroundBoxInput" type="text" v-model="backgroundBox">
            <label for="textColorInput">Color de texto: </label>
            <input id="textColorInput" type="text" v-model="textColor">
            <label for="mostrarTextoCheck">Mostrar texto: </label>
            <input id="mostrarTextoCheck" type="checkbox" v-model="showTexto">
            <label for="borderTextoRange">Borde: </label>
            <input id="borderTextoRange" type="range" min="0" max="10" v-model="borderBox">

        </div>
        <div class="box" :style="{ backgroundColor: backgroundBox, border: borderBox + 'px solid' }">
            <p :style="{ color: textColor }" v-show="showTexto">Awesome Vue.js</p>
        </div>
    </div>
</template>

<style>
.container {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    gap: 10px;
    width: 100%;
    max-width: 100%;
    margin: 0 auto;
}

.selectores,
.box {
    flex: 1;
    display: flex;
    flex-direction: column;
}

.selectores {
    justify-content: center;
}

.box {
    height: 100px;
    width: 100px;
    border: 1px;
}
</style>
