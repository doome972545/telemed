<template>
    <div id="page" class="site">
        <div class="container">
            <nav>
                <ul>
                    <li :class="{ 'active': activeIndex === index }" v-for="(item, index) in items" :key="index"
                        @click="setActive(index)">
                        <a href="#" :id="item.text">
                            <span class="icon"><feather-icon :icon="item.icon" size="30"></feather-icon></span>
                            <span class="text">{{ item.text }}</span>
                        </a>
                    </li>
                </ul>
            </nav>
            <section>
                <div v-if="activeIndex === 0">
                    <Profile></Profile>
                </div>
                <div v-if="activeIndex === 1">
                    <h2>reccord</h2>
                </div>
                <div v-if="activeIndex === 2">
                    <h2>appointment</h2>
                </div>
                <div v-if="activeIndex === 3">
                    <h2>test</h2>
                </div>
            </section>
        </div>
    </div>
</template>

<script>
import Profile from "./Profile.vue"
import FeatherIcon from '@/@core/components/feather-icon/FeatherIcon.vue';
export default {
    components: {
        FeatherIcon,
        Profile,
    },
    data() {
        return {
            activeIndex: 0, // เริ่มต้น active index เป็น 0
            items: [
                { icon: 'UserIcon', text: 'บัญชี' },
                { icon: 'FileTextIcon', text: 'บันทึก' },
                { icon: 'HomeIcon', text: 'นัดหมาย' },
                { icon: 'HomeIcon', text: 'test' }
            ]
        };
    },
    methods: {
        setActive(index) {
            this.activeIndex = index;
        }
    }
}
</script>

<style scoped>
ul {
    list-style: none;
}

.container {
    max-width: 100%;
    margin: 0 auto;
}

nav {
    position: fixed;
    bottom: 0%;
    width: 100%;
    padding-right: 30px;
    margin-left: -15px;
    background: #e3e3e3;
    border-radius: 15px;

}

nav ul {
    display: flex;
    align-items: center;
    justify-content: space-around;
}

a {
    color: #000;
}

nav ul li a {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
    text-align: center;
    font-weight: 500;
}

nav ul li a .icon {
    position: relative;
    display: block;
    line-height: 75px;
    font-size: 1.5em;
    text-align: center;
    transition: 0.5s;
}

nav ul li.active a .icon {
    transform: translateY(-10px);
    color: #c1b763;
}

nav ul li a .text {
    position: absolute;
    font-size: 1.2em;
    bottom: 10%;
    font-weight: 400;
    letter-spacing: 0.05em;
    transition: 0.5s;
    width: 100px;
    opacity: 0;
    transform: translateY(20px);
}

nav ul li.active a .text {
    opacity: 1;
    transform: translateY(10px);
    color: #c1b763;

}
</style>