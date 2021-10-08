# Vtex Utils

### 1. Todos os produtos: ###
```html
http://minhaloja.com.br/api/catalog_system/pub/products/search/
```

### 2. Produto por ID: ###
```html
http://minhaloja.vtexcommercestable.com.br/api/catalog_system/pub/products/search/?fq=productId:10440
```

### 3. Produto por categoria: ###
```html
http://minhaloja.com.br/api/catalog_system/pub/products/search/perfume
```

### 4. Todas as categorias: ###
```html
http://minhaloja.com.br/api/catalog_system/pub/category/tree/3
```

### 5. Meus pedidos (Necessário usar Header, keys e etc): ###
```html
http://minhaloja.vtexcommercestable.com.br/api/oms/pvt/orders/583003059415-01
```

### 6. Buscar todos produtos: ###
```html
http://www.minhaloja.com.br/busca/?fq=0
```

### 7. Variações do produto: ###
```html
/api/catalog_system/pub/products/variations/66
```

### 8. Buscar pelo EAN: ###
```html
http:/minhaloja.vtexcommercestable.com.br/api/catalog_system/pub/products/search?fq=alternateIds_Ean:7898526205947
```

### 9. OrderForm: ###
```javascript
vtexjs.checkout.getOrderForm().done(function(orderForm) {

	var orderFormId = orderForm.orderFormId;

	$.ajax({
	url: '/api/checkout/pub/orderForm/'+orderFormId+'/items/0/price',
	type: 'PUT',
	headers: header,  
	data:'{"price":'+total+'}',                          
	success: function(data) {
		console.log('Ok!')
	}
});

$.ajax({                 
	url: '/api/checkout/pub/orderForm/'+orderFormId+'/attachments/clientProfileData',
	type: 'POST',
	headers: header,
	data: '{"attachmentId": "clientProfileData","email": "'+$("#accountEmail").val()+'","firstName": "'+novo1+'","lastName": "'+novo2+'","document": "'+$('#accountCpfNumber').val()+'","documentType": "cpf","phone": "'+$('#accountCell').val()+'","corporateName": null,"tradeName": null,"corporateDocument": null,"stateInscription": null,"corporatePhone": null,"isCorporate": false}',
	success: function() {
		console.log('Ok!')
	} 
});

$.ajax({
	url: '/api/checkout/pub/orderForm/'+orderFormId+'/attachments/shippingData',
	type: 'POST',
	headers: header,
	data: '{"attachmentId": "shippingData","address": {"addressType": "residential","addressId": "-1368194386810","receiverName": "'+$.cookie('NOME')+'","postalCode": "'+$("#accountCep").val()+'","city": "'+$('#accountsity option:selected').val()+'","state": "'+$('#accountstate option:selected').val()+'","country": "BRA","street": "'+$('#accountaddress').val()+'","number": "'+$('#accountnumber').val()+'","neighborhood": "'+$('#accountdistrict').val()+'","complement": "'+$('#accountcomplement').val()+'","reference": null},}',
	success: function() {
		console.log('Ok!')
	} 
});

```

### 10. Produto por marca: ###
```html
/api/catalog_system/pub/products/search/?fq=B:<id_marca>
```

### 11. Produto por coleção: ###
```html
/api/catalog_system/pub/products/search/?fq=H:<id_colecao>
```

### 12. Busca categoria, coleção e faixa de preço ###
```html
/busca/?fq=C:4&fq=H:100&fq=P:[20TO50]
```

### 13. Linkando mais de uma coleção: ###
```html
/135/147/148?map=productClusterSearchableIds,productClusterSearchableIds,productClusterSearchableIds
```

### 14. Cálculo de frete: ###
```javascript
// O `items` deve ser um array de objetos que contenham, no mínimo, as informações abaixo

var items = [{
	id: 20,  // sku do item
	quantity: 1,
	seller: '1'
}];

// O `postalCode` deve ser o CEP do cliente, no caso do Brasil
var postalCode = '06416070';

// O `country` deve ser a sigla de 3 letras do país
var country = 'BRA';

vtexjs.checkout.simulateShipping(items, postalCode, country)
  .done(function(result) {
	/* `result.logisticsInfo` é um array de objetos.
	   Cada objeto corresponde às informações de logística (frete) para cada item,
	     na ordem em que os items foram enviados.
	   Por exemplo, em `result.logisticsInfo[0].slas` estarão as diferentes opções
	     de transportadora (com prazo e preço) para o primeiro item.
	   Para maiores detalhes, consulte a documentação do orderForm.
	*/

	alert('Transportadoras e valores');
	console.log(result.logisticsInfo[0].slas);
});
```

### 15. Informações de endereço pelo CEP: ###
```javascript
// O `postalCode` deve ser o CEP do cliente, no caso do Brasil
var postalCode = '06416070';

// O `country` deve ser a sigla de 3 letras do país
var country = 'BRA';

var address = {
	postalCode: postalCode,
	country: country
};

vtexjs.checkout.getAddressInformation(address)
  .done(function(result) {
    console.log(result);
});

```

### 16. Compre junto: ###
```html
http://minhaloja.vtexcommercestable.com.br/comprejuntosku/19
```

### 17. Ajax múltiplos: ###
```javascript
$.when($.getJSON(graphUSER), $.getJSON(graphPOSTS)).done(function (user, posts) { });
```

### 18. Profile: ###
```html
https://www.loja.com.br/api/checkout/pub/profiles/?email=email@bonito.com&sc=1
```

### 19. Pedido (Get): ###
```html
/api/checkout/pub/orders/v1104098smpr-01
```

### 20. Info do cliente logado: ###
```html
/no-cache/profileSystem/getProfile
```

### 21. Infos orderForm: ###
```html
http://minhaloja.vtexcommercestable.com.br/api/checkout/pub/orderForm
```

### 22. Busca página: ###
```html
http://minhaloja.cl/buscapagina?sl=481c7748-cdc5-44f0-93c2-6ecf4cccc4ee&PS=7&cc=7&sm=0&PageNumber=3&fq=H:138
```

### 23. URLs orders: ###
```html
https://documenter.getpostman.com/view/94611/oms/Hs41#e-c5c7-d934-c232-b37f7b774635
```

### 24. URLs Logistics: ###
```html
https://documenter.getpostman.com/view/3848/logistics/Hs42
```

### 25. URLs pricing: ###
```html
https://documenter.getpostman.com/view/3442/pricing/Hs8L
```

### 26. PCI: ###
```html
https://documenter.getpostman.com/view/322855/pci/Hs3y
```

### 27. Attachment: ###
```javascript
vtexjs.checkout.getOrderForm().then(function(orderForm) {
    var shippingData = orderForm.shippingData;
    shippingData.availableAddresses.splice(1, 1);
    return vtexjs.checkout.sendAttachment('shippingData', shippingData);
}).done(function(orderForm) {
    console.log('orderForm alterado!', orderForm, orderForm.shippingData);
});
```

### 28. Busca por múltiplos skus ###
```html
https://minhaloja.com/api/catalog_system/pub/products/search/?fq=skuId:625&fq=skuId:28 
```

### 29. API de similares, quem comprou, comprou tbm e etc ###
```html
https://documenter.getpostman.com/view/845/search-103/Hs43#e8e08b8f-4036-bfa0-8196-e8267683300a
```

### 30. Fazer um pedido regular usando as APIs ###
```html
http://help.vtex.com/pt/tutorial/fazer-um-pedido-regular-usando-as-apis-da-vtex
```

### 31. API Pública de pedidos
```html
/api/oms/pub/user/user@email.com.br/orders/numeroDoPedido
```

### 32. Observa alteração no OrderForm
```javascript
$(window).on('orderFormUpdated.vtex', function() {
   console.log('OrderForm updated!')
});
```

### 33. Simulação de frete
```javascript
function getSla(id, zipCode) {
    var DataToSend = {
        'items': [{
            'id': id,
            'quantity': 1,
            'seller': '1'
        }],
        'postalCode': zipCode,
        'country': 'BRA',
    };

    $.ajax({
        'type': 'POST',
        'dataType': 'json',
        'contentType': 'application/json',
        'url': '/api/checkout/pub/orderForms/simulation/?sc=1',
        'data': JSON.stringify(DataToSend),
        'success': function(ResponseData) {
           `//CUSTOM` function
	    createTable(ResponseData)
        },
        'error': function(AjaxError) {
	    console.log('Error')
        }
    });
}
```
## Authors

| [<img src="https://avatars2.githubusercontent.com/u/4562886?v=4&s=130" width="130px;"><br><sub>@felipe-ssilva</sub>](https://github.com/felipe-ssilva) |
| :---: |
