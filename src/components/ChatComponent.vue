<template>
    <div class="chat">
        <div class="chat-tap">
            <div class="chat-header">
                <img src="@images/user.svg" alt="user img">
                <p>
                    name 1
                    <span>last seen</span>
                </p>
            </div>
            <div class="chat-content">
                <ul>
                    <li class="received">
                        Hi
                        <span>Time</span>
                    </li>
                    <li class="received">
                        How are you?
                        <span>Time</span>
                    </li>
                    <li>
                        Hi
                        <span>Time</span>
                    </li>
                    <li v-if="text">
                        {{ text }}
                        <span>Time</span>
                    </li>
                </ul>
            </div>
        </div>
        <div class="input">
            <input type="text" placeholder="Message" ref="message" />

            <EmojiPicker
                picker-type="input"
                :native="false"
                :hide-search="true"
                :hide-group-names="true"
                :disable-skin-tones="true"
                @select="onSelectEmoji"
            />
            <div class="btn" @click="openImoji">
                <Icon icon="mingcute:emoji-line" />
            </div>
            <div class="btn" @click="sendMessage">
                <Icon icon="iconamoon:send-duotone" />
            </div>
        </div>
    </div>
</template>

<script setup>
// import picker compopnent
import EmojiPicker from 'vue3-emoji-picker';
// import css
import 'vue3-emoji-picker/css';

import { Icon } from '@iconify/vue';
import { ref } from 'vue';

const text = ref()
const message = ref(null)

const openImoji = _ => {
    document.querySelector('.v3-input-picker-wrap').classList.toggle('v3-picker-is-open')
}

const sendMessage = _ => {
    text.value = message.value.value
    message.value.value = ''
}

function onSelectEmoji(emoji) {
    document.querySelector('.v3-input-picker-wrap').classList.remove('v3-picker-is-open')
    message.value.value = message.value.value + String.fromCodePoint(parseInt(emoji.u, 16))
}
</script>

<style lang="scss" scoped>
.chat {
    background: transparent !important;
    position: relative;
    padding: 0 !important;
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    
    .chat-tap {
        height: 100%;
        background: $section-bg;
        border-radius: 14px;

        .chat-header {
            height: 4rem;
            width: 100%;
            border-radius: 14px;
            background: $header-bg;
            display: inline-flex;
            justify-content: flex-start;
            align-items: center;
            gap: 3rem;
            padding-inline: 1.5rem 3rem;
    
            img {
                height: 2.5rem;
            }
    
            p {
                width: 100%;
                display: inline-flex;
                justify-content: space-between;
            }
        }
    
        .chat-content {
            padding: 2rem;
    
            ul {
                display: flex;
                flex-direction: column;
                gap: 2rem;
    
    
                li {
                    color: $first-color;
                    position: relative;
                    width: fit-content;
                    padding: 0.5rem 2rem 0.5rem 1.5rem;
                    border-radius: 20px 5px 20px 5px;
                    background: $message1-bg;
                    align-self: flex-end;
                    
                    &.received {
                        border-radius: 5px 20px 5px 20px;
                        background: $message2-bg;
                        align-self: flex-start;
    
                        span {
                            font-size: 0.75rem;
                            position: absolute;
                            bottom: -1rem;
                            inset-inline-end: 0;
                            inset-inline-start: unset;
                        }
                    }
                    
                    span {
                        color: $second-color;
                        font-size: 0.75rem;
                        position: absolute;
                        bottom: -1rem;
                        inset-inline-start: 0;
                    }
                }
            }
        }
    }

    .input {
        display: inline-flex;
        align-items: center;
        justify-content: space-between;
        width: 100%;
        height: 2.5rem;
        border-radius: 14px;
        background: $header-bg;
        
        input {
            width: 100%;
            padding: 0.5rem 2rem;
            background: transparent;
            color: $main-color;
            outline: none;
            border: none;

            &::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
                color: rgba($main-color, 0.7);
                opacity: 1; /* Firefox */
            }

            &:-ms-input-placeholder { /* Internet Explorer 10-11 */
                color: rgba($main-color, 0.7);
            }

            &::-ms-input-placeholder { /* Microsoft Edge */
                color: rgba($main-color, 0.7);
            }
        }
        
        .v3-input-emoji-picker {
            :deep(.v3-emoji-picker-input),
            :deep(.v3-input-picker-icon),
            :deep(.v3-footer) {
                display: none;
            }

            :deep(.v3-emoji-picker) {
                inset: unset !important;
                transform: none !important;
                bottom: 1.5rem !important;
                inset-inline-end: -2rem !important;
            }
        }

        .btn {
            border-radius: 50%;
            background: $message1-bg;
            padding: 0.25rem;
            margin-inline: 0.5rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 2rem;
            height: 2rem;
            
            svg {
                font-size: 1.5rem;
            }
        }
    }
}
</style>