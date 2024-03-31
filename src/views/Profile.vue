<template>
    <div>
        <h1>Profiles s</h1>
        <button @click="nextpage">test</button>
    </div>
</template>

<script>
import { useRouter } from 'vue-router';
import liff from '@line/liff';
import api from '@/api';

export default {
    data() {
        return {
            displayName: "",
            pictureUrl: "",
            userId: "",
            email: "",
        };
    },
    setup() {
        // liff.init({
        //     liffId: "2004241454-6y3Rqy2R"
        // }).then(() => {
        //     if (liff.isLoggedIn()) {
        //         liff.getProfile().then(userProfile => {
        //             this.displayName = userProfile.displayName;
        //             this.pictureUrl = userProfile.pictureUrl;
        //             this.userId = userProfile.userId;
        //             this.email = liff.getDecodedIDToken().email;
        //         this.checkUser()
        //         }).catch(error => {
        //             console.error("Failed to retrieve profile:", error);
        //         });
        //     } else {
        //         liff.login()
        //     }
        // })
    },
    mounted() {
    },
    methods: {
        nextpage() {
            this.$router.push({ name: "register" });
        },

        checkUser() {
            api.post('/login', {
                displayName: this.displayName,
                pictureUrl: this.pictureUrl,
                Uid: this.userId,
                email: this.email
            }, {
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': 'Bearer ' + localStorage.getItem('access_token')
                }
            }).then((response) => {
                if (response.statuscode == 200) {
                    console.log("user registration")
                } else {
                    this.$router.push({
                        name: "register", params: {
                            displayName: this.displayName,
                            email: this.email,
                            pictureUrl: this.pictureUrl,
                            userId: this.userId,
                        }
                    });
                }
            });

        }
    }
}
</script>

<style></style>