<template>
    <div class="contacts">
        <h4>Contacts</h4>

        <ul>
            <li class="online">
                <div>
                    <img src="@images/user.svg" alt="user img">
                </div>
                <p>
                    name 1
                    <span>last seen</span>
                </p>
            </li>
            <li>
                <img src="@images/user.svg" alt="user img">
                <p>
                    name 2
                    <span>last seen</span>
                </p>
            </li>
        </ul>
    </div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.contacts {
    width: 25%;
    position: relative;

    h4 {
        position: absolute;
        top: -1rem;
        inset-inline-start: 2rem;
        background: $main-bg;
        padding: 0.25rem 0.5rem;
        border-radius: 14px;
    }

    ul {
        margin-top: 1.5rem;
        display: flex;
        flex-direction: column;
        gap: 2rem;

        li {
            padding-inline: 1.5rem 1rem;
            width: 100%;
            display: inline-flex;
            align-items: center;
            gap: 1rem;

            &.online {
                div::after {
                    content: '';
                    position: absolute;
                    width: 0.5rem;
                    height: 0.5rem;
                    border-radius: 50%;
                    background: #00c700;
                }
            }
            
            img {
                width: 3rem;
                height: 3rem;
            }
    
            p {
                width: 100%;
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                
                span {
                    text-align: end;
                }
            }
        }
    }
}
</style>