<template>
    <div>
        <p class="mb-2 text-2xl">Dialog</p> 
        <div>
            <MyDialog :visible="dialogVisible" @backdrop-clicked="switchDialog">
                <template #title>
                    <p class="font-bold">Dialog</p>
                </template>
                <template #body>
                    honbun
                </template>
                <template #footer>
                    <div class="flex justify-end">
                        <SecondaryButton @click="switchDialog">close</SecondaryButton>
                    </div>
                </template>
            </MyDialog>
        </div>
        <div class="mb-2">
            <PrimaryButton @click="switchDialog">open</PrimaryButton>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import PrimaryButton from '../buttons/PrimaryButton.vue';
import SecondaryButton from '../buttons/SecondaryButton.vue';
import MyDialog from './MyDialog.vue'

export default defineComponent({
    name: 'DialogSample',
    components: {
        PrimaryButton,
        SecondaryButton,
        MyDialog,
    },
    setup() {
        const dialogVisible = ref(false);
        const switchDialog = () => {
            dialogVisible.value = !dialogVisible.value;
        };

        return {
            dialogVisible,
            switchDialog,
        };
    },
});

</script>
