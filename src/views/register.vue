<template>
    <div>
        <h1>Register</h1>
        <p>{{ $route.params.displayName }}</p>
        <p>{{ $route.params.email }}</p>
        <p>{{ email }}</p>
        <button @click="register">register</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            email: "",
        }
    },
    created() {
        // ดึงข้อมูลจาก params ที่ถูกส่งมา
        const { displayName, email, pictureUrl, userId } = this.$route.params;
        this.email = email;
    },
    mounted() {
        // this.register()
    },
    method: {
        register() {
            api.post('/register', {
                email: this.email
            }, {
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': 'Bearer ' + localStorage.getItem('access_token')
                }
            }).then((response) => {
                console.log(response.data)
            }).catch((error) => {
                console.log(error)
            })
        }
    }
};
</script>

<style>
/* CSS สำหรับคอมโพเนนต์นี้ */
</style>