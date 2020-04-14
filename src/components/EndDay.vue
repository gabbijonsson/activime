<template>
    <div class="end-day--container">
        <p>Klar för idag?</p>
        <img src="../assets/img/icon--action-endday.svg" alt="Avsluta-ikon">
    </div>
</template>

<script>
export default {
    name: 'EndDay'    
}
</script>

<style scoped>
p {
    display: inline;
    font-size: 2em;
}

.end-day--container {
  display: block;
  position: fixed;
  bottom: 10em;
  width: 100vw;
}

</style>