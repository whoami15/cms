<template>
    <div class="range-fieldtype-wrapper bg-grey-20 rounded py-1 px-2 border">
        <div class="flex items-center">
            <div v-if="config.prepend" v-text="config.prepend" class="mr-1" />
            <input
                type="range"
                v-model="val"
                :name="name"
                :min="config.min"
                :max="config.max"
                :step="config.step"
                :width="config.width"
                :readonly="isReadOnly"
                :disabled="isReadOnly"
                :id="fieldId"
                class="flex-1"
            />
            <div class="rounded border px-1 py-sm mx-1 bg-grey-10">{{ val }}</div>
            <div v-if="config.append" v-text="config.append" />
        </div>
    </div>
</template>

<script>
import Fieldtype from './Fieldtype.vue';

export default {

    mixins: [Fieldtype],

     data() {
        return {
            val: this.value || (this.config.max - this.config.min) / 2
        }
    },

    watch: {
        val(value) {
            this.update(value);
        }
    }

}
</script>
