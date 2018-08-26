Authentication vs Authorization
==
### Authentication 鑑別
判斷使用者是不是他所宣稱的那個人，
如帳號密碼機制，是基於帳號密碼為只有本人跟系統本身才知道的 shared secret，所以只要可以正確輸入密碼，系統就可判斷使用者為這個帳號所代表的人物。
主要回答這些問題： 
Who is the user?
Is the user really who he/she represents himself to be?

### Authorization 授權
判斷當前使用者所擁有對系統資源存取的權限(等級)，例如會員登入後擁有讀寫資源的權力，而訪客只有讀的權力。
主要回答這些問題： 
Is user X authorized to access resource R?
Is user X authorized to perform operation P?
Is user X authorized to perform operation P on resource R?

### Identification 識別
判斷使用者是誰，Identification必須是獨一無二的，才能正確的分辨出每個人。

主要回答這些問題： 
Who is the user?

### 上面三者的關係：
系統要知道某個使用者對系統資源的存取權力，包含三個部分
使用者告訴系統他是誰(Identification 機制)。
例：輸入ID
系統判斷使用者是否真的是他宣稱的那個人(Authentication 機制)
例：輸入Password
系統根據該帳號所擁有的權限驗證該使用者(Auorization 機制)
例：系統判斷該使用者為會員，給予讀及寫的權利

### Reference
[Link](http://2010end.blogspot.com/2010/12/authentication-vs-authorization.html)