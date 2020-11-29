<template>
    <div class="clock">
        <p class="date">{{ date }}</p>
        <p class="time">{{ time }}</p>
    </div>
</template>

<script>
    
    export default {
        name: "clock",
        data () {
            return {
                date: '',
                time: '',
                week: ['SUN', 'MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT']
            }
        },
        mounted () {
            setInterval(this.updateTime, 1000)
        },
        components: {
        },
        methods: {
            updateTime() {
                let cd = new Date();
                this.time = this.zeroPadding(cd.getHours(), 2) + ':' + this.zeroPadding(cd.getMinutes(), 2) + ':' + this.zeroPadding(cd.getSeconds(), 2);
                this.date = this.zeroPadding(cd.getDate(), 2) + '.' + this.zeroPadding(cd.getMonth()+1, 2) + '.' + this.zeroPadding(cd.getFullYear(), 4) + ' ' + this.week[cd.getDay()];
            },
            zeroPadding(num, digit) {
                let zero = '';
                for(var i = 0; i < digit; i++) {
                    zero += '0';
                }
                return (zero + num).slice(-digit);
            }
        }
    }
</script>
