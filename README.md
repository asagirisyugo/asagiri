# asagiri


<!DOCTYPE HTML>
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:th="http://www.thymeleaf.org">

<head th:fragment="header (title)">
  <title th:text="${title}">title</title>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <link th:href="@{/lib/bootstrap/css/bootstrap.css}" rel="stylesheet" />
  <!-- jQuery読み込み -->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
  <script src="/lib/bootstrap/css/bootstrap.min.js"></script>
</head>
<body>
<style>
input{
width:80px!important;
}


</style>

<script>
$(function(){
	$(document).on( 'click', '.firstBtn', function(){ 
		var tr = $(this).parent().parent(); // クリックしたtdの親trを得る
		tr.after('<tr><td  rowspan="1" class="left2"><input class="btn btn-default firstBtn" type="button" value="追加"  /><a class="btn btn-secondary">削除</a></td><td  rowspan="1" class="left2"><input type="text" name="fluit[0]" value="りんご"></td><td  rowspan="1"  class="left2"><input type="text" name="quantity[0]" value="3"></td><td><input class="btn btn-default lastBtn" type="button" value="追加"  /><a class="btn btn-secondary">削除</a></td><td><input type="text" name="fluit[0]" value="りんご"></td><td><input type="text" name="quantity[0]" value="3"></td></tr>'); // 親trの後ろに追加したい行を入れる

		//tr.children().first().attr("rowSpan", row);
		tr.find(".left").each( function( index, element ) {

			var row = $(this).attr('rowSpan')+1;
			$(this).attr("rowSpan", row);
		 
		})
	});
	$(document).on( 'click', '.lastBtn', function(){ 
		var tr = $(this).parent().parent(); // クリックしたtdの親trを得る
		tr.after('<tr><td><input class="btn btn-default lastBtn" type="button" value="追加"  /><a class="btn btn-secondary">削除</a></td><td><input type="text" name="fluit[0]" value="りんご"></td><td><input type="text" name="quantity[0]" value="3"></td></tr>'); // 親trの後ろに追加したい行を入れる

		//tr.children().first().attr("rowSpan", row);
		tr.find(".left2").each( function( index, element ) {
			var row = $(this).attr('rowSpan')+1;
			$(this).attr("rowSpan", row);
		 
		})
	});
});

</script>

<div class="container">
<br>
<br>
<br>
<br>
  <form th:action="@{/save}" method="post">
	<input class="btn btn-default" type="submit" value="登録" />
	<table class="table table-bordered">
	  <thead>
		<tr>
		  <th>日付</th>
		  <th>Firstボタン</th>
		  <th>果物</th>
		  <th>数量</th>
		  <th>LAstボタン</th>
		  <th>果物</th>
		  <th>数量</th>
		</tr>
	  </thead>
	  <tbody>
		<tr>
		  <td rowspan="1" class="left left2"><input type="text" name="date" value="りんご"></td>
		  <td  rowspan="1" class="left2">
			 <input class="btn btn-default firstBtn" type="button" value="追加"  />
			 <a class="btn btn-secondary">削除</a>
		  </td>
		  <td  rowspan="1" class="left2"><input type="text" name="fluit[0]" value="りんご"></td>
		  <td  rowspan="1"  class="left2"><input type="text" name="quantity[0]" value="3"></td>
		  
		  <td>
			<input class="btn btn-default lastBtn" type="button" value="追加"  />
			 <a class="btn btn-secondary">削除</a>
		  </td>
		  <td><input type="text" name="fluit[0]" value="りんご"></td>
		  <td><input type="text" name="quantity[0]" value="3"></td>
		</tr>
	  </tbody>
	</table>
  </form>
</div>

</body>
</html>
