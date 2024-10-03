<script>
export default {
    name: 'Projects',
    data() {
        return {
            
        };
    }
};
</script>


<template>
    <h1>Home</h1>
    <div>
        <nav>
            <ul>
                <li>
                    <router-link :to="{name: 'home'}">Home</router-link>
                </li>
                <li>
                    <router-link :to="{name: 'projects'}">Projects</router-link>
                </li>
                <li>
                    <router-link :to="{name: 'contacts'}">Contacts</router-link>
                </li>
            </ul>
        </nav>
    </div>
</template>


<style lang="scss">

</style>