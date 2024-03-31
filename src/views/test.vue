<template>

</template>

<script>
import api from '@/api'
export default {
    // เริ่มทำก่อน
    data() {
        return {
            id: null,
            email: 'john@example.com',
            password: "1234",
        }
    },
    setup() {

    },
    // param
    created() {
        const queryString = window.location.search
        const urlParams = new URLSearchParams(queryString)
        this.id = urlParams.get('id')
        // console.log(this.id)
    },
    // 
    mounted() {
        this.loadData()
    },
    methods: {
        loadData() {
            const params = { id: this.id, email: this.email, password: this.password }
            api.post('/linelogin', params, {
                headers:
                {
                    'Content-Type': 'application/json',
                    Authorization: 'Bearer ' + localStorage.getItem('access_token')
                },
            }).then((response)=>{
                console.log(response.data)
                this.$router.push({ name: "home" , query: {id:this.id}});
            }).catch((error)=>{
                console.log(error)
            })
        }
    }
}
</script>

<style>

</style>