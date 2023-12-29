# -.github.io

1. frmCriteria.jsp 에서 주소창에 type, keyword도 붙게 하려고 시도했다.

2. <input type="hidden" name="type" value="${pageMaker.criteria.type}">
<input type="hidden" name="keyword" value="${pageMaker.criteria.keyword}"> 를 추가.

3.
frmCriteria.jsp

<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
    

<form id="frmCriteria" action="#" method="get">

<input type="hidden" name="pageNum" value="${pageMaker.criteria.pageNum}">
<input type="hidden" name="amount" value="${pageMaker.criteria.amount}">
<input type="hidden" name="bno" value="${param.bno}">
<input type="hidden" name="type" value="${pageMaker.criteria.type}">
<input type="hidden" name="keyword" value="${pageMaker.criteria.keyword}">
			
</form>

4.

내가 바란 거 : http://localhost/board/get?pageNum=1&amount=10&bno=500&type=&keyword=
나온 결과 : 검색어를 입력해주세요. 메세지창 뜬다. 

5. 원인은 

var keyword = $("[name=keyword]").val();
		if (keyword.trim() == "") {
			alert("검색어를 입력해주세요.");
			$("[name=keyword]").focus();
			return false;
		}
		

var elkeyword = $(this).find("[name=keyword]").val(); 을 만들지 않았다. var elkeyword 를 만들어 준 다음에
keyword 로 넘겨 줄 수 있도록 해야 한다. 
