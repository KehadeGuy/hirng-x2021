<template>
    <div v-if="userData">
        <p class="heading__1">{{userData.name}}</p>
        <div>
            <img src="../assets/imagery.jpg" alt="img" class="imagery">
        </div>
        <div class="footer_menu">
            <div class="logo_area">
                <a href="">
                    <img src="../assets/face.jpg" alt="">
                </a>
            </div>
            <div class="footer_inner_main_menu">
                <ul>
                    <li>
                        <router-link to="/">
                            Home
                        </router-link>
                    </li>
                    <li>
                        <router-link to="/">
                            About
                        </router-link>
                    </li>
                    <li>
                        <router-link to="/">
                            Gallery
                        </router-link>
                    </li>
                    <li>
                        <router-link to="/">
                            Contact
                        </router-link>
                    </li>
                </ul>
            </div>
        </div>
        <div class="sticky-container">
        <ul class="sticky">
            <li>
                <a :href="`https://www.instagram.com/${userData.social_media.instagram}`" :title="`${userData.social_media.instagram}`" target="_blank" rel="noreferrer noopener">
                    <img src="../assets/instagram.svg" width="32" height="32">
                </a>
            </li>
            <li>
                <a :href="`https://www.twitter.com/${userData.social_media.twitter}`" :title="`${userData.social_media.twitter}`" target="_blank" rel="noreferrer noopener">
                    <img src="../assets/tweeter.svg" width="32" height="32">
                </a>
                
            </li>
            <li>
                <a :href="`https://www.snapchat.com/${userData.social_media.snapchat}`" :title="`${userData.social_media.snapchat}`" target="_blank" rel="noreferrer noopener">
                    <img src="../assets/snapchat.svg" width="32" height="32">
                </a>
                
            </li>
            <li>
                <a :href="`mailto:${userData.social_media.email}`" :title="`${userData.social_media.email}`">
                    <img src="../assets/envelope.svg" width="32" height="32">
                </a>
                
            </li>
            
        </ul>
</div>
    </div>
</template>

<script>
    import axios from 'axios'
    import '../assets/css/style.css'

    export default {
        name: "landing",
        data(){
            return{
                link:'www.facebook.com',
                userData: null
            }
        },
        methods: {
            getResponse() {
                axios.get('https://hirng-x2021.glitch.me/api')
                .then(response => {
                    this.userData = response.data
                    console.log(response);
                }).catch(error => {
                    console.log(error);
                })
            }
        },
        mounted() {
            this.getResponse()
        }
    }
</script>
