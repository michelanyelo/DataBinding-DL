<script>
export default {
    name: 'DataBinding',
    data() {
        return {
            backgroundBox: '',
            textColor: '',
            showTexto: false,
            borderBox: '0',
            borderRadiusBox: '0',
            borderColor: '',
            textContent: '',
            typoStyle: '',
            fontStyle: ['normal', 'italic', 'oblique'],
            opacityBox: false
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
            <label for="mostrarTextCheck">Mostrar texto: </label>
            <input id="mostrarTextCheck" type="checkbox" v-model="showTexto">
            <label for="borderTextRange">Borde: </label>
            <input id="borderTextRange" type="range" min="0" max="10" v-model="borderBox">
            <label for="borderRadiusRange">Borde redondeado: </label>
            <input id="borderRadiusRange" type="range" min="0" max="50" v-model="borderRadiusBox">
            <label for="borderColorInput">Color de borde: </label>
            <input id="borderColorInput" type="text" v-model="borderColor">
            <label for="textContentInput">Contenido Textual: </label>
            <input id="textContentInput" type="text" v-model="textContent">
            <label for="typoTextSelect">Tipografía: </label>
            <select id="typoTextSelect" v-model="typoStyle">
                <option v-for="(style, idx) in fontStyle" :key="idx" :value="style">{{ style }}</option>
            </select>
            <label for="opacityBoxCheck">Opaco: </label>
            <input id="opacityBoxCheck" type="checkbox" v-model="opacityBox">
        </div>
        <div :class="{ 'box-block': backgroundBox }" :v-show="!backgroundBox"
            :style="{ backgroundColor: backgroundBox, border: borderBox + 'px solid', borderRadius: borderRadiusBox + 'px', borderColor: borderColor, opacity: opacityBox ? 1 : 0.5 }">
            <p :style="{ color: textColor, fontStyle: typoStyle }" v-show="showTexto">{{ textContent }}</p>
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

.box-none {
    display: none;
}

.box-block {
    display: block;
    width: 400px;
    height: 400px;
}
</style>
