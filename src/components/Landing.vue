<template>
    <div>
        <div v-if="loading" class="loading">
            <h1>Loading....</h1>
        </div>
        <div v-else>
            <p class="heading__1">{{userData.name}}</p>
            <div>
                <img src="../assets/imagerry.png" alt="img" class="imagery">
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
    </div>
</template>

<script>
    import axios from 'axios'
    import '../assets/css/style.css'

    export default {
        name: "landing",
        data(){
            return{
                userData: null,
                loading: false
            }
        },
        methods: {
            async getResponse() {

                // Please wait while loading is true
                this.loading = true

                try {
                    const response = await axios.get('https://hirng-x2021.glitch.me/api')

                    // Loading is done
                    this.loading = false
                    
                    // Assign response data to userData
                    this.userData = response.data
                } catch (error) {

                    // Loading done
                    this.loading = false

                    // If any error exists log in on the console
                    console.log(error.response);
                }
            }
        },
        mounted() {
            // Call method once page is ready
            this.getResponse()
        }
    }
</script>
