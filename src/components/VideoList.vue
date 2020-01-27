<template>
    <ul class="list-group col-md-4">
        <VideoListItem 
            :key = "video.etag" 
            v-for = "video in videos"
            :video = "video"
            @videoSelect="onVideoSelect"
        >
            {{video}}
        </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem';
export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: ['videos'],
    methods: {
        onVideoSelect(video){
            this.$emit('videoSelect', video);
        }
    }
}
</script>

<style>

</style>