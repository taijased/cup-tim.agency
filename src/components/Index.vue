<template lang="pug">
   .wrapper(:class="{'black-bg': !color, 'white-bg': color}")
        transition-group(name="fade-in-top", mode="in-out", tag="header")
            .status(v-if="color", key="top-black") Site in progress
            .status(v-else, key="top-white") Site in progress
        main 
            transition-group(name="fade-in-left", mode="in-out")
                .status(v-show="color", @click="colorBlack()", key="left-black", class="hover-underline") Black
                .status(v-show="!color", @click="colorWhite()", key="left-white", class="hover-underline") White
        .main-title 
            transition-group(name="fade-in-bottom", mode="in-out")
                .title(v-if="color", key="bottom-2-black")
                    .letter t
                    .letter i
                    .letter m
                    .space
                    .letter a
                    .letter g
                    .letter e
                    .letter n
                    .letter c
                    .letter y
                .title(v-else, key="bottom-2-white")
                    .letter t
                    .letter i
                    .letter m
                    .space
                    .letter a
                    .letter g
                    .letter e
                    .letter n
                    .letter c
                    .letter y
        .mail 
            transition-group(name="fade-in-bottom", mode="in-out", tag="footer")
                .status(v-if="color", key="bottom-2-black", class="hover-underline")
                    a(href="mailto:hello@tim.agency.ru") hello@<br/>tim.agency
                .status(v-else, key="bottom-2-white", class="hover-underline") 
                    a(href="mailto:hello@tim.agency.ru") hello@<br/>tim.agency
        transition-group(name="fade-in-bottom", mode="in-out", tag="footer")
            .status(v-if="color", key="bottom-1-black") Say hello:
            .status(v-else, key="bottom-1-white") Say hello:
        aside 
            transition-group(name="fade-in-right", mode="out-in")
                .correct(v-if="color", key="right-black") 
                    .design design
                    .creative creative
                .correct(v-else, key="right-white") 
                    .design design
                    .creative creative

</template>

<script>
export default {
    data () {
        return {
            color: true,
            status: 'Black'
        }
    },
    methods: {
        colorBlack () {
            this.status = 'White'
            this.color = false
        },
        colorWhite () {
            this.status = 'Black'
            this.color = true
        }
    }
}
</script>

<style lang="stylus">
.wrapper
    color white
    display grid
    grid-template-rows 0.4fr 1.7fr 1.5fr 1.15fr 0.6fr 1.3fr 0.4fr
    grid-template-columns 0.31fr 2.3fr 1.3fr 1fr 0.06fr
    height 100vh
    width 100vw
    overflow hidden
    header 
        grid-column-start 2
        grid-column-end 3
        grid-row-start 2
        grid-row-end 3
    main 
        grid-column-start 2
        grid-column-end 3
        grid-row-start 3
        grid-row-end 5
        display flex
        flex-direction row
        justify-content flex-start
        align-items center
    .main-title 
        grid-column-start 2
        grid-column-end 3
        grid-row-start 5
        grid-row-end 6
    footer 
        grid-column-start 2
        grid-column-end 3
        grid-row-start 6
        grid-row-end 7
        display flex
        flex-direction row
        justify-content flex-start
        align-items flex-end
    .mail 
        grid-column-start 3
        grid-column-end 4
        grid-row-start 6
        grid-row-end 7
        display flex
        flex-direction row
        justify-content flex-start
        align-items flex-end
        margin-left -40px
    aside 
        grid-column-start 4
        grid-column-end 5
        grid-row-start 2
        grid-row-end 7


$lp = 10%
$tm = .3s
$bg-time = .5s
$mp = 50px

.wrapper
    header 
        .status 
            position absolute
            font-family 'TT Norms Regular'
            font-size 16px
    main 
        .status 
            position absolute
    .main-title
        .title 
            position absolute
            margin-top -35px
            display flex
            flex-direction row
            justify-content flex-start
            align-items center
            @media (max-width: 1300px)
                margin-top -25px
            @media (max-width: 1024px)
                margin-top -15px
            @media (max-width: 768px)
                margin-top -5px
            @media (max-width: 425px)
                margin-top 15px
            
            .letter 
                font-family 'TT Norms Bold'
                font-size 115px
                @media (max-width: 1300px)
                    font-size 100px 
                @media (max-width: 1024px)
                    font-size 90px 
                @media (max-width: 768px)
                    font-size 70px 
                @media (max-width: 425px)
                    font-size 36px
                    letter-spacing 0px
                text-transform uppercase
                transform translate(0, 0)
                transition transform $tm
                letter-spacing -2px
                &:hover 
                    cursor default
                    transform translate(0, -25px)
                    transition transform $tm
            .space 
                height 100%
                width 30px
    aside 
        font-family 'TT Norms Bold'
        font-size 100px
        @media (max-width: 1300px)
            font-size 100px 
        @media (max-width: 1024px)
            font-size 90px 
        @media (max-width: 1000px)
            font-size 80px 
        @media (max-width: 768px)
            display none       
        text-transform uppercase
        transition color $bg-time
        .correct 
            position absolute
            bottom 0
            right 0
        .design 
            position absolute
            right 0
            bottom 182px
            transform rotate(-90deg)
            z-index 99
        .creative
            position absolute
            right -173px
            bottom 242px
            transform rotate(-90deg)
            z-index 99
    footer 
        font-family 'TT Norms Regular'
        font-size 16px
        .status 
            position absolute
            a 
                text-decoration none
                color inherit
    .hover-underline
        display inline-block
        position relative
        &::after 
            content ''
            position absolute
            width 100%
            transform scaleX(0)
            height 2px
            bottom 0
            left 0
            transform-origin bottom right
            transition transform 0.25s ease-out
        &:hover 
            cursor pointer
            &::after 
                transform scaleX(1)
                transform-origin bottom left
        
.black 
    color #000
    transition color $bg-time

.white 
    color #fff
    transition color $bg-time
.black-bg
    background #000
    color #fff
    background-image: url(../assets/grid-black.png) ;
    background-position: center center;
    background-repeat:  no-repeat;
    background-attachment: fixed;
    background-size:  cover;
    transition background $bg-time, color $bg-time
    .hover-underline 
        color #fff
        &::after 
            background-color #fff
    aside 
        color #1C1B1C
        transition color $bg-time

.white-bg
    background #fff
    color #000
    background-image: url(../assets/grid-white.png) ;
    background-position: center center;
    background-repeat:  no-repeat;
    background-attachment: fixed;
    background-size:  cover;
    transition background $bg-time, color $bg-time
    .hover-underline 
        color #000
        &::after 
            background-color #000
    aside 
        color #EEEDEE
        transition color $bg-time


    
</style>

