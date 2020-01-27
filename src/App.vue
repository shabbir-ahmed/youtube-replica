<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoDetails :video="video"></VideoDetails>
        <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetails from './components/VideDetails';
const API_KEY = 'AIzaSyBbLKsyE3pP14OVIcH-w_FjMiUvYAyFfF8';

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetails
    },
    data(){
        return { videos: [] };
    },
    methods: {
        onVideoSelect(video){
            // eslint-disable-next-line no-console
            console.log(video);
            this.video = video;
        },
        onTermChange(searchTearm){

            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTearm
                } 
            }).then(response => {
                this.videos = response.data.items;
            });
            
        }
    }
}
</script>