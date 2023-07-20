<template>
    <div>
        <h2>Users</h2>
        <p>사용자: {{ userInfo.userid }}</p>
        <p>사용자 롤: [{{ userInfo.roles.join(', ')}}]</p>
        <button @click="logout">로그아웃</button>
    </div>
</template>

<script>
import { getUserInfo,logoutProcess } from '../utils/AuthUtil';
import { useRouter } from 'vue-router'

export default {
    name:'Admins',
    setup() {
        const router = useRouter();
        const userInfo = getUserInfo();
        const logout = () => {
            logoutProcess(()=>{
                router.push({name:'home'});
            })
        }
    
        return {userInfo, logout}
    }
}
</script>