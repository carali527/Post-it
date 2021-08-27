<template>
    <label for="red"
    >Red：
    <input
        id="red"
        type="text"
        placeholder="0 to 255."
        maxlength="3"
        size="7"
        :value="red"
        @input="$emit('update:red', $event.target.value)"
        oninput = "value=value.replace(/[^\d]/g,'')"
        required
        />
    <slot name='red'></slot></label>
    <label for="green"
    >Green：  
    <input
        id="green"
        type="text"
        placeholder="0 to 255."
        maxlength="3"
        size="7"
        :value="green"
        @input="$emit('update:green', $event.target.value)"
        oninput = "value=value.replace(/[^\d]/g,'')"
        required
    />
    <slot name='green'></slot>
    </label>
    <label for="blue"
    >Blue：
    <input
        id="blue"
        type="text"
        placeholder="0 to 255."
        maxlength="3"
        size="7"
        :value="blue"
        @input="$emit('update:blue', $event.target.value)"
        oninput = "value=value.replace(/[^\d]/g,'')"
        required
    />
    <slot name='blue'></slot>
    </label>
</template>

<script>
export default {
  props: ["blue","red","green"],
  emits: ["update:blue","update:red","update:green"]
}
</script>