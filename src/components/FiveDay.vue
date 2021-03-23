<template>
<div :key="weather.visibility" v-for="weather in weatherFive">
    <h3>{{weather.visibility}}</h3>
</div>
</template>

<script>
export default {
    name: 'FiveDay',
    props: {
        weatherFive: Object,
    }
}
</script>