<script type="text/javascript" src="/CRM/SiteAssets1/TrafficLight/jquery-1.11.1.min.js"></script>
<script type="text/javascript">

//La unción se ejecuta cada que se carga la página  
jQuery(document).ready(function(){
  
  
//Función para onbtener la fecha del día en que se consulta la página y darle el formato dd/mm/YYYY
var currentDate = new Date();
var day = currentDate.getDate();
var month = currentDate.getMonth() + 1;
var year = currentDate.getFullYear();
var actualDate =  month + "/" + day + "/" + year;

//Este alert puede usarse para comprobar la salida de la fecha
//alert("Esta es la Fecha Actual:"+ actualDate);


//Este loop revisa cada una de las 
jQuery("span.ms-noWrap").each(function(){
 
var modifDate =jQuery(this).html();
//alert(" Fecha de  Modificacion:" + modifDate);
  
var date1 = new Date(modifDate);
var date2 = new Date(actualDate);


var timeDiff = Math.abs(date2.getTime()- date1.getTime());
var tiempoTrans =timeDiff/(1000*3600*24);

//Alerts de Prueba para revisar que el valor sea correcto
//alert(date1 + date2 + "Han pasado :" +  timeDiff/(1000*3600*24) + " días");
//alert("Han pasado :" +  tiempoTrans + " días");

var bigContainer = jQuery(this).closest(".ms-itmhover");
var lightCell  = bigContainer.find("div.ms-number");

jQuery(lightCell).append(tiempoTrans);

});

jQuery("div.ms-number").each(function() {

  var divNormal = jQuery(this).html();
  var divInteger = parseInt(divNormal); 
  
     //var status = "";
  if(divInteger <=5){
        //Si el elemento tiene de 0 a 5 días desde su modificación
   jQuery(this).append('<img class="estatus" src="https://nisisoft694.sharepoint.com/CRM/Imgenes/verde.png"/>');
    }
   if(divInteger >6 && divInteger < 15 ){
      //Si el elemento tiene de 6 a 15 días desde su modificación
    jQuery(this).append('<img class="estatus" src="https://nisisoft694.sharepoint.com/CRM/Imgenes/amarillo.png"/>');
    }
   if (divInteger >=16){
    //Si el elemento tiene mas de 15 días desde su modificación
    jQuery(this).append('<img class="estatus" src="https://nisisoft694.sharepoint.com/CRM/Imgenes/rojo.png"/>');
   }
 
});



});
     
</script>
