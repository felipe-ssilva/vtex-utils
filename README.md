# Vtex urls

### Lista de URLs da plataforma Vtex ###

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

### 5. Meus pedidos (Header, keys e etc): ###
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

### 9. Produto por SKU: ###
```html
http://minhaloja.vtexcommercestable.com.br/produto/sku/6865
```

### 10. OrderForm: ###
```html
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

### 11. Produto por marca: ###
```html
/api/catalog_system/pub/products/search/?fq=B:<id_marca>
```

### 12. Produto por coleção: ###
```html
/api/catalog_system/pub/products/search/?fq=H:<id_colecao>
```

### 13. Página de coleção: ###
```html
/busca?fq=H:139
```

### 14. Linkando mais de uma coleção: ###
```html
http://www.loja.com.br/135/147/148?map=productClusterSearchableIds,productClusterSearchableIds,productClusterSearchableIds
```

### 15. Cálculo de frete: ###
```html
// O `items` deve ser um array de objetos que contenham, no mínimo, as informações abaixo

var items = [{
	id: 20,  // sku do item
	quantity: 1,
	seller: '1'
}];

// O `postalCode` deve ser o CEP do cliente, no caso do Brasil
var postalCode = '06416070';
// Desse jeito também funciona
// var postalCode = '22250040';

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

### 16. Informações de endereço pelo CEP: ###
```html
// O `postalCode` deve ser o CEP do cliente, no caso do Brasil
var postalCode = '06416070';
// Desse jeito também funciona
// var postalCode = '22250040';

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

### 17. Compre junto: ###
```html
http://minhaloja.vtexcommercestable.com.br/comprejuntosku/19
```

### 18. Ajax multiplos: ###
```html
$.when($.getJSON(graphUSER), $.getJSON(graphPOSTS)).done(function (user, posts) { });
```

###19. Profile: ###
```html
https://www.loja.com.br/api/checkout/pub/profiles/?email=email@bonito.com&sc=1
```

### 20. Pedidos (Get): ###
```html
/api/checkout/pub/orders/
```

### 21. Pedido (Get): ###
```html
/api/checkout/pub/orders/v1104098smpr-01
```

### 22. Info do cliente logado: ###
```html
/no-cache/profileSystem/getProfile
```

### 23. Infos orderForm: ###
```html
http://minhaloja.vtexcommercestable.com.br/api/checkout/pub/orderForm
```

### 24. Busca página: ###
```html
http://minhaloja.cl/buscapagina?sl=481c7748-cdc5-44f0-93c2-6ecf4cccc4ee&PS=7&cc=7&sm=0&PageNumber=3&fq=H:138
```

### 25. URLs orders: ###
```html
https://documenter.getpostman.com/view/94611/oms/Hs41#e-c5c7-d934-c232-b37f7b774635
```

### 26. URLs Logistics: ###
```html
https://documenter.getpostman.com/view/3848/logistics/Hs42
```

### 27. URLs pricing: ###
```html
https://documenter.getpostman.com/view/3442/pricing/Hs8L
```

### 28. PCI: ###
```html
https://documenter.getpostman.com/view/322855/pci/Hs3y
```

### 29. Attachment: ###
```html
vtexjs.checkout.getOrderForm().then(function(orderForm) {
    var shippingData = orderForm.shippingData;
    shippingData.availableAddresses.splice(1, 1);
    return vtexjs.checkout.sendAttachment('shippingData', shippingData);
}).done(function(orderForm) {
    console.log('orderForm alterado!', orderForm, orderForm.shippingData);
});
```
