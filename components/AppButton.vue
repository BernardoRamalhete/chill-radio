<template>
    <button class="main-button">
        <span class="hover top one"/>
        <span class="hover top two"/>
        <span class="hover top three"/>
        <span class="hover top four"/>
        <span class="hover top five"/>
        <span class="hover top six"/>
        <span class="hover top seven"/>
        <span class="hover top eight"/>
        <span class="hover top-center one"/>
        <span class="hover top-center two"/>
        <span class="hover top-center three"/>
        <span class="hover top-center four"/>
        <span class="hover top-center five"/>
        <span class="hover top-center six"/>
        <span class="hover top-center seven"/>
        <span class="hover top-center eight"/>
        <span class="hover center one"/>
        <span class="hover center two"/>
        <span class="hover center three"/>
        <span class="hover center four"/>
        <span class="hover center five"/>
        <span class="hover center six"/>
        <span class="hover center seven"/>
        <span class="hover center eight"/>
        <span class="hover bottom-center one"/>
        <span class="hover bottom-center two"/>
        <span class="hover bottom-center three"/>
        <span class="hover bottom-center four"/>
        <span class="hover bottom-center five"/>
        <span class="hover bottom-center six"/>
        <span class="hover bottom-center seven"/>
        <span class="hover bottom-center eight"/>
        <span class="hover bottom one"/>
        <span class="hover bottom two"/>
        <span class="hover bottom three"/>
        <span class="hover bottom four"/>
        <span class="hover bottom five"/>
        <span class="hover bottom six"/>
        <span class="hover bottom seven"/>
        <span class="hover bottom eight"/>
        
        <span class="background">
            <slot/>
        </span>
        
        <span class="glass">
            <slot/>
        </span>

    </button>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.main-button {
    outline: transparent;
    position: relative;
    border: none;
    background-color: transparent;

    .background {
        display: block;
        background-color: $gray;
        padding: 12px 28px;
        border-radius: 8px;
        width: 100%;
        height: 100%;
        color: transparent;
        user-select: none;
    }

    .hover {
        position: absolute;
        width: 12.5%;
        height: 20%;
        z-index: 1;
        cursor: pointer;
        &:hover {
            & ~ .glass {
                background-color: rgba(whitesmoke, 0.2);
                background-image: radial-gradient(transparent, rgba(whitesmoke, 0.6)), url('/images/background-noise.png');
                backdrop-filter: blur(4px);
                border-color: $pure_white;
            }
        }
        &.top {
            top: 0;
            &.one {
                &:hover {
                    & ~ .background {
                        transform: translate(35px, 10px);
                    }
                }
            }
            &.two {
                &:hover {
                    & ~ .background {
                        transform: translate(25px, 10px);
                    }
                }
            }
            &.three {
                &:hover {
                    & ~ .background {
                        transform: translate(15px, 10px);
                    }
                }
            }
            &.four {
                &:hover {
                    & ~ .background {
                        transform: translate(5px, 10px);
                    }
                }
            }
            &.five {
                &:hover {
                    & ~ .background {
                        transform: translate(-5px, 10px);
                    }
                }
            }
            &.six {
                &:hover {
                    & ~ .background {
                        transform: translate(-15px, 10px);
                    }
                }
            }
            &.seven {
                &:hover {
                    & ~ .background {
                        transform: translate(-25px, 10px);
                    }
                }
            }
            &.eight {
                &:hover {
                    & ~ .background {
                        transform: translate(-35px, 10px);
                    }
                }
            }
            &-center {
                &.one {
                    &:hover {
                        & ~ .background {
                            transform: translate(35px, 12px);
                        }
                    }
                }
                &.two {
                    &:hover {
                        & ~ .background {
                            transform: translate(25px, 12px);
                        }
                    }
                }
                &.three {
                    &:hover {
                        & ~ .background {
                            transform: translate(15px, 12px);
                        }
                    }
                }
                &.four {
                    &:hover {
                        & ~ .background {
                            transform: translate(5px, 12px);
                        }
                    }
                }
                &.five {
                    &:hover {
                        & ~ .background {
                            transform: translate(-5px, 12px);
                        }
                    }
                }
                &.six {
                    &:hover {
                        & ~ .background {
                            transform: translate(-15px, 12px);
                        }
                    }
                }
                &.seven {
                    &:hover {
                        & ~ .background {
                            transform: translate(-25px, 12px);
                        }
                    }
                }
                &.eight {
                    &:hover {
                        & ~ .background {
                            transform: translate(-35px, 12px);
                        }
                    }
                }
            }
        }
        &.top-center {
            top: 20%;
        }
        &.center {
            top: 40%;
            &.one {
                &:hover {
                    & ~ .background {
                        transform: translate(35px, 14px);
                    }
                }
            }
            &.two {
                &:hover {
                    & ~ .background {
                        transform: translate(25px, 14px);
                    }
                }
            }
            &.three {
                &:hover {
                    & ~ .background {
                        transform: translate(15px, 14px);
                    }
                }
            }
            &.four {
                &:hover {
                    & ~ .background {
                        transform: translate(5px, 14px);
                    }
                }
            }
            &.five {
                &:hover {
                    & ~ .background {
                        transform: translate(-5px, 14px);
                    }
                }
            }
            &.six {
                &:hover {
                    & ~ .background {
                        transform: translate(-15px, 14px);
                    }
                }
            }
            &.seven {
                &:hover {
                    & ~ .background {
                        transform: translate(-25px, 14px);
                    }
                }
            }
            &.eight {
                &:hover {
                    & ~ .background {
                        transform: translate(-35px, 14px);
                    }
                }
            }
        }
        &.bottom-center {
            top: 60%;
        }
        &.bottom {
            top: 80%;
            &.one {
                &:hover {
                    & ~ .background {
                        transform: translate(35px, 18px);
                    }
                }
            }
            &.two {
                &:hover {
                    & ~ .background {
                        transform: translate(25px, 18px);
                    }
                }
            }
            &.three {
                &:hover {
                    & ~ .background {
                        transform: translate(15px, 18px);
                    }
                }
            }
            &.four {
                &:hover {
                    & ~ .background {
                        transform: translate(5px, 18px);
                    }
                }
            }
            &.five {
                &:hover {
                    & ~ .background {
                        transform: translate(-5px, 18px);
                    }
                }
            }
            &.six {
                &:hover {
                    & ~ .background {
                        transform: translate(-15px, 18px);
                    }
                }
            }
            &.seven {
                &:hover {
                    & ~ .background {
                        transform: translate(-25px, 18px);
                    }
                }
            }
            &.eight {
                &:hover {
                    & ~ .background {
                        transform: translate(-35px, 18px);
                    }
                }
            }
            &-center {
                &.one {
                    &:hover {
                        & ~ .background {
                            transform: translate(35px, 16px);
                        }
                    }
                }
                &.two {
                    &:hover {
                        & ~ .background {
                            transform: translate(25px, 16px);
                        }
                    }
                }
                &.three {
                    &:hover {
                        & ~ .background {
                            transform: translate(15px, 16px);
                        }
                    }
                }
                &.four {
                    &:hover {
                        & ~ .background {
                            transform: translate(5px, 16px);
                        }
                    }
                }
                &.five {
                    &:hover {
                        & ~ .background {
                            transform: translate(-5px, 16px);
                        }
                    }
                }
                &.six {
                    &:hover {
                        & ~ .background {
                            transform: translate(-15px, 16px);
                        }
                    }
                }
                &.seven {
                    &:hover {
                        & ~ .background {
                            transform: translate(-25px, 16px);
                        }
                    }
                }
                &.eight {
                    &:hover {
                        & ~ .background {
                            transform: translate(-35px, 16px);
                        }
                    }
                }
            }
        }
        &.one {
            left: 0;
        }
        &.two {
            left: 12.5%;
        }
        &.three {
            left: 25%;
        }
        &.four {
            left: 37.5%;
        }
        &.five {
            left: 50%;
        }
        &.six {
            left: 62.5%;
        }
        &.seven {
            left: 75%;
        }
        &.eight {
            left: 87.5%;
        }
    }

    .glass {
        position: absolute;
        inset: 0;
        border-radius: 8px;
        background-color: transparent;
        backdrop-filter: blur(0);
        display: grid;
        place-items: center;
        white-space: nowrap;
        font-size: 18px;
        font-weight: 500;
        border: 1px solid transparent;
        transition: all 0.3s ease;
    }


    &.primary {
        .background {
            background-color: $light_blue;
            transition: all 0.3s ease;
        }
    }

    &.icon {
        .background {
            font-size: 24px;
            padding: 2px 6px;
        }
        .glass {
            font-size: 24px;
        }
    }
    
    &.danger {
        .background {
            background-color: $primary_red;
        }
        .glass {
            color: $pure_white;
        }
    }
}
</style>