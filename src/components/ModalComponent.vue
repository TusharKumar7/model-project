<template>
    <div class="main-container" @click.self="$emit('showModal')">
        <div :class="[theme === 'sale' && 'sale-theme-modal', 'modal-container']">
            <div :class="[theme === 'sale' && 'sale-theme-title', 'modal-title']">
                {{ title }}
            </div>
            <div :class="[theme === 'sale' && 'sale-theme-content', 'modal-content']">
                {{ content }}
            </div>
            <slot></slot>
            <div class="modal-links">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "ModalComponent",
    props: {
        title: String,
        content: String,
        theme: String,
    },
};
</script>

<style scoped>
.main-container {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7);
    cursor: pointer;
    position: absolute;
    z-index: 1;
}

.modal-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 30px;
    border-radius: 10px;
    gap: 30px;
    background: #fff;
    box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
        rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
    width: 25%;
    margin: 0 auto;
    position: absolute;
    inset: 0;
    top: 30%;
    height: max-content;
    z-index: 2;
    cursor: default;
}

.sale-theme-modal {
    background: #ec283a;
}

.modal-title {
    font-size: 1.5rem;
    font-weight: 600;
    color: #05b7b0;
}

.sale-theme-content,
.sale-theme-title {
    color: #fff;
}

.modal-links {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
}
</style>
