<script>
export default {
    name: 'header'
}
</script>

<template>
    <div class="pesq">
        <input type="text" class="form-control" placeholder="Pesquisar cidade especifica" aria-label="Recipient's username"
            aria-describedby="button-addon2">
        <button class="btn btn-secondary" type="button" id="button-addon2">Button</button>
    </div>
</template>

<style>
.pesq{
    display: flex;
    padding: 5px;
    border-radius: 5px;
    background-color: rgb(255, 255, 255);
}
.form-control{
    background-color: none !important;
    border: none !important;
}
button{
    color:white;
    background-color: rgb(82, 24, 75) !important;
}

</style>