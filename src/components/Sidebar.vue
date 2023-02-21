<template>
    <aside :class="`${is_expanded && 'is-expanded'}`">
        <div class="logo">
            <img src="../assets/vue.svg" alt="Vue">
        </div>

        <div class="menu-toggle-wrap">
            <button class="menu-toggle">
                <span class="material-icons" @click="ToggleMenu">
                    keyboard_double_arrow_right
                </span>
            </button>
        </div>

        <h3>MENU</h3>
        <div class="menu">
            <router-link class="button" to="/">
                <span class="material-icons">home</span>
                <span class="link-text">Home</span>
            </router-link>
            <router-link class="button" to="/about">
                <span class="material-icons">description</span>
                <span class="link-text">About</span>
            </router-link>
        </div>
    </aside>
</template>

<script setup>
    import { ref } from "vue"

    const is_expanded = ref(false)

    const ToggleMenu = () => {
        is_expanded.value = !is_expanded.value
    }
</script>

<style lang="scss" scoped>
    aside {
        display: flex;
        flex-direction: column;
        width: calc(2rem + 32px);
        min-height: 100vh;
        overflow: hidden;
        padding: 1rem;

        background-color: var(--dark);
        color: var(--light);

        transition: 0.2s ease-out;

        .logo {
            margin-bottom: 1rem;

            img {
                width: 2rem;
            }
        }

        .menu-toggle-wrap {
            display: flex;
            justify-content: flex-end;
            margin-bottom: 1rem;

            position: relative;
            top: 0;
            transition: 0.2s ease-out;

            .menu-toggle {
                transition: 0.2s ease-out;

                .material-icons {
                    font-size: 2rem;
                    color: var(--grey);
                    transition: 0.2s ease-out;
                }

                &:hover {
                    .material-icons {
                        color:var(--light);
                        transform: translateX(0.2rem);
                    }
                }
            }
        }

        h3, .button .link-text {
            opacity: 0;
            transition: 0.3s ease-out;
        }

        h3 {
            color: var(--grey);
            font-size: 0.875rem;
            margin-bottom: 0.5rem;
        }

        .menu {
            margin: 0 -1rem;

            .button {
                display: flex;
                align-items: center;
                text-decoration: none;

                padding: 0.5rem 1rem;
                transition: 0.2 ease-out;

                .material-icons {
                    font-size: 2rem;
                    color: var(--grey);
                    transition: 0.2s ease-out;
                }

                .link-text {
                    color: var(--grey);
                    transition: 0.2s ease-out;
                }

                &:hover, &.router-link-exact-active {
                    background-color: var(--dark-alt);

                    .material-icons, .link-text {
                        color: var(--light);
                    }
                }

                &.router-link-exact-active {
                    border-right: 5px solid var(--light);
                }
            }
        }

        &.is-expanded {
            width: var(--sidebar-width);

            .menu-toggle-wrap {
                top: -3rem;
                .menu-toggle {
                    transform: (rotate(-180deg));
                }
            }

            h3, .button .link-text {
            opacity: 1;
        }

        .button {
            .material-icons {
                margin-right: 1rem;
            }
        }
        }

        @media (max-width: 768px) {
            position: fixed;
            z-index: 99;
        }
    }

</style>