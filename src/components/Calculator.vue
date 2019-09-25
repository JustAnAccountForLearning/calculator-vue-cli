<template>
    <div class="caclulator">
        <h1>{{ msg }}</h1>
    </div>
</template>

<script>
export default {
  name: 'Calculator',
  props: {
    msg: String
  }
}
</script>