<template>
    <div>
        <button @click="$emit('changeOperator', '+')">Addition<br/>+</button>
        <button @click="$emit('changeOperator', '-')">Substraction<br/>-</button>
        <button @click="$emit('changeOperator', '/')">Division<br/>/</button>
        <button @click="$emit('changeOperator', '*')">Multiplication<br/>X</button>
    </div>
</template>
<script>
export default {
    
}
</script>
<style>
    button {
        padding: 20px;
        margin-right: 20px;
        width: 160px;
        height: 80px;
        background-color: #BFAF7E;
        color: #401C14;
        font-size: 15px;
        cursor: pointer;
        vertical-align: top;
    }
</style>