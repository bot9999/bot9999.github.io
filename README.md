# bot9999.github.io
				$.ajax({
                type: "GET",
                url: "https://api.coinmarketcap.com/v1/ticker/?convert=KRW",
				contentType: 'application/x-www-form-urlencoded, charset=utf-8',
                dataType: "json",
                success: function(result){
					var chk = getQuerystring('sb')
					chk = chk.toUpperCase();
					var i, name= "";
					var i, rank= 0;
					var i, price_btc= 0;
					var i, price_krw= 0;
					var i, price_usd= 0;
					var i, percent_change_1h= 0;
					var i, percent_change_24h= 0;
					for (i = 0; i < 100; i++) { 
					if(result[i].symbol == chk){
					name = result[i].name;
					rank = Number(result[i].rank);
					price_btc = Number(result[i].price_btc);
					price_krw = Number(result[i].price_krw);
					price_usd = Number(result[i].price_usd);
					percent_change_1h = Number(result[i].percent_change_1h);
					percent_change_24h = Number(result[i].percent_change_24h);
					}
					
					}
					var tag ="(coinmarketcap기준)<br>"+name+"("+rank+"위)<br>USD : $"
					+price_usd.toFixed(4)+"("+percent_change_1h+"%)<br>BTC : "
					+price_btc+"<br>KRW : "+price_krw.toFixed(2)+"원<br> 24시간전 ("+percent_change_24h+"%)";
					$("#target").html(tag);
                },
            error: function(err){
                alert(err);
            }
            });    
        return false;
	});
function getQuerystring(paramName){ 
var _tempUrl = window.location.search.substring(1);
var _tempArray = _tempUrl.split('&');
  for(var i = 0; _tempArray.length; i++) {
	 var _keyValuePair = _tempArray[i].split('=');
	 if(_keyValuePair[0] == paramName){ 
	 return _keyValuePair[1]; 
	 } 
  } 
