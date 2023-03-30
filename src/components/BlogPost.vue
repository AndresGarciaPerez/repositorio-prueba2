
<script setup>

    defineProps(['title', 'id', 'body', 'colorText'])

</script>

<template>
<h1>Prueba de modificacion para github</h1>
    <div class="card">
        <div class="card-body">
            <h5  class="card-title" :class="`text-${colorText}`" >{{ id }} - {{ title }}</h5>
            <p>{{ body }}</p>
        </div>
    </div>
</template>