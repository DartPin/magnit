<template>
  <div id="app">
    
    <div class="akt-block" v-for="item of data" :key="item.liter">
      Заполняется в двух экземплярах (для представителя агентства и администрации магазина)
      <div class="akt-block__header">Акт о проведении работ демонтаж/монтаж РИМ out/indoor</div>
      <div class="akt-block__adress">Адрес магазина {{item.adress}} <br>
      Город {{item.city}}
      </div>

      <table class="akt-block__table">
        <tr>
          <td>Вид работ</td>
          <td>Всего шт.</td>
        </tr>
        <tr>
          <td>1. Демонтаж ФБ размер {{item.size}} мм <br>
            2. Монтаж ФБ размер {{item.size}} мм
          </td>
          <td>
            1 <br> 1
          </td>
        </tr>
      </table>

      <div class="akt-block__pret">
        Демонтированный ФБ "____________________________________________" {{item.size}} мм передан в ГМ. Претензий нет. <br>
        
      </div>
      <div class="akt-block__pret">
        
        ФБ {{item.size}} мм "_____________________________________________" монтирован на конструкцию {{item.liter}}. Сертификат соответствия и образец полотна переданы. Претезий нет
      </div>

      <div class="akt-block__footer">
        <div class="akt-block__footer__date">
          Дата _______________________
        </div>

        Сотрудник магазина ______________________________________________ (ФИО, подпись)<br>
        <div class="akt-block__footer__warn">(Подпись и печать магазина обязательна)</div>

        Представитель распространителей _____________________________________________ (ФИО, подпись)

      </div>
    </div>  
  </div>
</template>

<script>
import axios from "axios";


export default {
  name: "app",
  data() {
    return {
      data: []
    };
  },
  components: {
    
  },
  mounted() {
    axios
      .get("http://localhost:8081/")
      .then(
        response => (
          (this.data = response.data)
        )
      );
  },
  computed:{ 
  }
};
</script>

<style>
#app, html, body{
  float: none !important;
}
  .akt-block{
    font-size: 25px;
    padding: 10px;
    page-break-after: always;
  }
  .akt-block__header{
    width: 100%;
    text-align: center;
    margin: 80px 0 50px 0;
     font-weight: bold;
  }

  .akt-block__adress{
    margin: 30px 0 50px 0;
  }
  .akt-block__table{
    width: 90%;
    border: 1px solid black;
    margin: 0px 0 50px 0;
    border-collapse: collapse;
    
  }
  td{
    border: 1px solid black;
  }
  .akt-block__footer{
    margin: 50px 0 50px 0;  
  }
  .akt-block__footer__warn{
    width: 100%;
    text-align: center;
    font-weight: bold;
    font-size: 15px;
    margin: 0px 0 50px 0;
  }
  .akt-block__pret{
    margin: 0 0 30px 0;
  }
  .akt-block__footer__date{
    margin: 0 0 30px 0;
  }
  
</style>



