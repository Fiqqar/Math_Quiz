<template>
    <div>
        <button @click="$emit('changeOperator', '+')">Addition<br/>+</button>
        <button @click="$emit('changeOperator', '-')">Substraction<br/>-</button>
        <button @click="$emit('changeOperator', '/')">Division<br/>/</button>
        <button @click="$emit('changeOperator', 'X')">Multiplication<br/>X</button>
    </div>
</template>
<script>
export default {
    
}
</script>
<style>
</style>