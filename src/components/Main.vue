<template>
    <div class="main-page">
        <div class="primary">
            <div class="primary-menu">

                <div class="primary-header header">
                    <div class="clock-wrapper">
                        <clock></clock>
                    </div>
                    <div class="order-counter">Заказы: {{ordersNumber}}</div>
                </div>

                <div class="primary-menu-container">
                    <div class="main-buttons-container">
                        <div class="button-container">
                            <div class="main-button global-button" v-on:click="openSubmenu(0)">ТЕКУЩИЕ ЗАКАЗЫ</div>
                            <div class="submenu" v-show="submenuVisibles[0]">
                                <div class="submenu-button global-button">В работе</div>
                                <div class="submenu-button global-button">В ожидании</div>
                                <div class="submenu-button global-button">Готовые</div>
                            </div>
                        </div>
                        <div class="button-container">
                            <div class="main-button global-button" v-on:click="openSubmenu(1)">КОНТРАГЕНТЫ</div>
                            <div class="submenu" v-show="submenuVisibles[1]">
                                <div class="submenu-button global-button">Заказчики</div>
                                <div class="submenu-button global-button">Поставщики</div>
                            </div>
                        </div>                    
                        <div class="button-container">
                            <div class="main-button global-button" v-on:click="openSubmenu(2)">УСЛУГИ / ТОВАРЫ</div>
                            <div class="submenu" v-show="submenuVisibles[2]">
                                <div class="submenu-button global-button">Виды работ</div>
                                <div class="submenu-button global-button">Товары</div>
                            </div>
                        </div>
                        <div class="button-container">
                            <div class="main-button global-button" v-on:click="openSubmenu(3)">ОПЛАТЫ</div>
                            <div class="submenu" v-show="submenuVisibles[3]">
                                <div class="submenu-button global-button">Наличка</div>
                                <div class="submenu-button global-button">Безнал</div>
                                <div class="submenu-button global-button">Картириджи</div>
                            </div>
                        </div> 
                    </div>
                </div>
                <div class="primary-footer">
                    <div class="footer-button global-button">ЗАКРЫТЫЕ ЗАКАЗЫ</div>
                </div>
            </div>
            <div class="devider"></div>
        </div>


        <div class="secondary">
            <div class="secondary-header header">               
            </div>    
            <h1>content</h1>	
        </div>
    </div>
</template>

<script>
    import modal from '@/components/modal/modal';
    import clock from '@/components/utils/clock';

    export default {
        name: "Main",
        data () {
            return {
                modalVisible: false,
                ordersNumber: 23,
                test: false,
                submenuVisibles: [false, false, false, false]
            }
        },
        components: {
            modal: modal,
            clock: clock
        },
        methods: {
            closeModal: function () {
		  		this.modalVisible = false;	  		
		  	},
            openSubmenu: function(index) {
                //вью не может рактивно поменять элемент массива .. поэтому через splice
               let newVisibility = !this.submenuVisibles[index];
               this.submenuVisibles.splice(index, 1, newVisibility); 
            } 
        }
    }
</script>
