<template>
    <div>
        {{ video.snippet.title }}
    </div>
</template>

<script>
export default {
    name: 'VideoDetails',
    props: ['video']
}
</script>