<template>
    <li>
        <h2>{{ name }} {{ friendIsFavorite ? '(favorite)' : ''}}</h2>
        <button @click="toggleFavorite">{{ friendIsFavorite ? 'Mark' : 'Unmark' }} as favorite</button>
        <button @click="toggleDetails">{{ deatilsAreVisible ? 'Hide' : 'Show' }} details</button>
        <ul v-if="deatilsAreVisible">
            <li><strong>Phone: </strong>{{ phoneNumber }}</li>
            <li><strong>Email: </strong>{{ emailAdress }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    // props: [
    //     'name', 
    //     'phoneNumber',
    //     'emailAdress'
    // ],
    props: {
        name: {
            type: String,
            required: true 
        },
        phoneNumber: {
            type: String,
            required: false,
            default: '000 0000 0000',
            validator: function(value) {
                return value.length > 5
            } 
        },
        emailAdress: String,
        isFavorite: Boolean
    },
    data() {
        return {
            deatilsAreVisible: false,
            friendIsFavorite: this.isFavorite
        };
    },
    methods: {
        toggleDetails() {
            this.deatilsAreVisible = !this.deatilsAreVisible;
        },
        toggleFavorite() {
            // this.friendIsFavorite = !this.friendIsFavorite;
            this.$emit('toggle-favorite')
        }
    }
};
</script>

<style>

</style>

