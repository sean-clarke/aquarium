<template>
    <div id="clock">
        <div id="time">
            {{ hours }}:{{ minutes | pad }}
        </div>
        <div id="date">
            {{ date }}
        </div>
    </div>
</template>

<script>
    export default {
        name: 'clock',
        props: [],
        mounted() {
            this.setTime();
            this.interval = setInterval(this.setTime, 1000);
        },
        filters: {
            pad: v => v.toString().padStart(2, '0')
        },
        methods: {
            setTime() {
                const date = new Date();
                this.hours = date.getHours();
                this.minutes = date.getMinutes();
                let strs = date.toLocaleDateString('en-US', {
                    weekday: 'short',
                    day: 'numeric',
                    month: 'short',
                    year: '2-digit'
                }).split(' ');

                let result = '';
                strs.forEach(s => result += s.charAt(0).toUpperCase() + s.substring(1) + ' ');
                this.date = result.substring(0, result.length - 1);
            }
        },
        data() {
            return {
                hours: '00',
                minutes: '00',
                date: '',
                part: ''
            };
        },
        beforeDestroy() {
            clearInterval(this.interval);
        }
    }
</script>

<style>
    #clock {
        display: flex;
        flex-direction: column;
    }

    #time {
        margin-bottom: 12px;
        font-size: 48px;
    }

    #date {
        font-size: 24px;
        margin-bottom: 24px;
    }
</style>
