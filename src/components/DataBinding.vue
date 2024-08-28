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
            fontStyle: ['normal', 'italic', 'oblique']
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


        </div>
        <div class="box"
            :style="{ backgroundColor: backgroundBox, border: borderBox + 'px solid', borderRadius: borderRadiusBox + 'px', borderColor: borderColor }">
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

.box {
    height: 100px;
    width: 100px;
}
</style>
