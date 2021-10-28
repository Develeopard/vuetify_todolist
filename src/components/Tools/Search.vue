<template>
    <v-text-field
    :value="$store.state.search"
    @input="$store.commit('setSearch', $event)"
    :class="{ 'closed' : searchClosed && !$store.state.search}"
    @focus="searchClosed = false"
    @blur="searchClosed = true"
    :disabled="$store.state.sorting"
    class="expanding-search mt-1"
    dense
    clearable
    placeholder="Search"
    filled
    prepend-inner-icon="mdi-magnify"
    ></v-text-field>
</template>

<script>
export default {
data(){
    return{
        searchClosed : true
    }
}
}
</script>

<style lang="scss">
    .expanding-search{
        transition: max-width .3s;
        .v-input__slot{
            cursor: pointer !important;
            &::before, &::after{
                border-color: transparent !important;
            }
        }

        &.closed{
            max-width: 45px;
            .v-input__slot{
                background: transparent !important;
            }
        }
    }
</style>