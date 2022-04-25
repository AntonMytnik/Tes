## (backend tasks)

№ 626a0dd5821853ecc9b9cfb0dcf9903e
***

### Подключение к БД:
|          |                                  |
|----------|----------------------------------|
| hostname | 31.31.196.31                     |
| username | u1520945_626a0dd                 |
| password | 626a0dd5821853ecc9b9cfb0dcf9903e |
| database | u1520945_t1_626a0dd5821853ecc9b9 |
| port     | 3306                             |
| charset  | utf-8                            |


# TASK_API_1
> Создать API, которое принимает GET параметр _id рецепта_ и возвращает c БД данные в JSON формате со следующей информацией: **name**(string), **cooking_time_in_minutes**(int) и **serves**(int)
>> ### Дополнительные баллы:
>> + Добавить в JSON поля **ingredients**(array) и **directions**(array) для указанного _recipe_id_

> ### Примеры запроса:
> + **HTTP:** GET /api/v1/get/recipe?recipe_id=1 HTTP/1.1 \
Host: localhost 
> ---
> + **cURL:** curl --location --request GET 'http://localhost/api/v1/get/recipe?recipe_id=1'
> ---
> + **PHP:** 
> $curl = curl_init(); \
curl_setopt_array($curl, array( \
CURLOPT_URL => 'http://localhost/api/v1/get/recipe?recipe_id=1', \
CURLOPT_RETURNTRANSFER => true, \
CURLOPT_ENCODING => '', \
CURLOPT_MAXREDIRS => 10, \
CURLOPT_TIMEOUT => 0, \
CURLOPT_FOLLOWLOCATION => true, \
CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1, \
CURLOPT_CUSTOMREQUEST => 'GET')); \
$response = curl_exec($curl); \
curl_close($curl); \
echo $response;

> ### Пример ответа:
> ```{"recipe_id":"1","recipe_name":"BROCCOLI BROWNIES","cooking_time_in_minutes":"45","serves":"12"}```
> 
>> ### Пример ответа (дополнительные баллы):
>> ```{"recipe_id":"1","recipe_name":"BROCCOLI BROWNIES","cooking_time_in_minutes":"45","serves":"12","ingredients":[{"measure":"3 ounces","ingredient":"semisweet chocolate"},{"measure":"1 cup","ingredient":"broccoli puree"},{"measure":"1\/2 cup","ingredient":"firmly packed brown sugar"},{"measure":"1\/4 cup","ingredient":"unsweetened cocoa powder"},{"measure":"2 tablespoons","ingredient":"butter"},{"measure":"2 tablespoons","ingredient":"pure vanilla extract"},{"measure":"2","ingredient":"large egg whites"},{"measure":"3\/4 cup","ingredient":"unbleached all-purpose flour"},{"measure":"1\/2 teaspoon","ingredient":"baking powder"},{"measure":"1\/2 teaspoon","ingredient":"salt"}],"directions":["Preheat oven to 350 degrees.","Mix ingredients together.","Put in 8x8 pan.","Cook for 35-40 minutes.","Cut and eat!"]}```

 
# TASK_API_2
> Создать API, которое принимает POST параметры **name**(string), **cooking_time_in_minutes**(int) и **serves**(int), создает поле в БД и возвращает сгенерированный id рецепта.
>> Дополнительные баллы:
>> + POST так же должен принимать **ingredients**(array) и **directions**(array), а API должно создавать эти поля в БД (Вы сможете правильность выполнения если сделали задание на дополнительные баллы в TASK_API_1).

> ### Примеры запроса:
> + **HTTP:** POST /api/v1/post/recipe HTTP/1.1 \
     Host: localhost \
     Content-Type: application/x-www-form-urlencoded \
     Content-Length: 64 \
     name=CREAM%20CHEESE%20ICING&cooking_time_in_minutes=10&serves=20
> ---
> + **cURL:** curl --location --request POST 'http://localhost/api/v1/post/recipe' \
     --header 'Content-Type: application/x-www-form-urlencoded' \
     --data-urlencode 'name=CREAM CHEESE ICING' \
     --data-urlencode 'cooking_time_in_minutes=10' \
     --data-urlencode 'serves=20'
> ---
> + **PHP:**
> $curl = curl_init(); \
curl_setopt_array($curl, array( \
CURLOPT_URL => 'http://localhost/api/v1/get/recipe', \
CURLOPT_RETURNTRANSFER => true, \
CURLOPT_ENCODING => '', \
CURLOPT_MAXREDIRS => 10, \
CURLOPT_TIMEOUT => 0, \
CURLOPT_FOLLOWLOCATION => true, \
CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1, \
CURLOPT_CUSTOMREQUEST => 'POST', \
CURLOPT_POSTFIELDS => 'name=CREAM%20CHEESE%20ICING&cooking_time_in_minutes=10&serves=20', \
CURLOPT_HTTPHEADER => array( \
'Content-Type: application/x-www-form-urlencoded' \
), \
)); \
$response = curl_exec($curl); \
curl_close($curl); \
echo $response;
>> ### Примеры запроса (дополнительные баллы):
>> + **HTTP:** POST /api/v1/get/recipe HTTP/1.1
     Host: localhost
     Content-Type: application/x-www-form-urlencoded
     Content-Length: 504
     name=CREAM%20CHEESE%20ICING&cooking_time_in_minutes=10&serves=20&directions%5B0%5D=Mix%20all%20ingredients%20together.&directions%5B1%5D=Enjoy.&ingredients%5B0%5D%5Bmeasure%5D=1%20package&ingredients%5B0%5D%5Bingredient%5D=cream%20cheese&ingredients%5B1%5D%5Bmeasure%5D=1%2F4%20cup&ingredients%5B1%5D%5Bingredient%5D=margarine&ingredients%5B2%5D%5Bmeasure%5D=1%20teaspoon&ingredients%5B2%5D%5Bingredient%5D=vanilla&ingredients%5B3%5D%5Bmeasure%5D=2%20cups&ingredients%5B3%5D%5Bingredient%5D=icing%20sugar
>> ---
>> + **cURL:** curl --location --request POST 'http://localhost/api/v1/get/recipe' \
     --header 'Content-Type: application/x-www-form-urlencoded' \
     --data-urlencode 'name=CREAM CHEESE ICING' \
     --data-urlencode 'cooking_time_in_minutes=10' \
     --data-urlencode 'serves=20' \
     --data-urlencode 'directions\[0]=Mix all ingredients together.' \
     --data-urlencode 'directions\[1]=Enjoy.' \
     --data-urlencode 'ingredients\[0]\[measure]=1 package' \
     --data-urlencode 'ingredients\[0]\[ingredient]=cream cheese' \
     --data-urlencode 'ingredients\[1]\[measure]=1/4 cup' \
     --data-urlencode 'ingredients\[1]\[ingredient]=margarine' \
     --data-urlencode 'ingredients\[2]\[measure]=1 teaspoon' \
     --data-urlencode 'ingredients\[2]\[ingredient]=vanilla' \
     --data-urlencode 'ingredients\[3]\[measure]=2 cups' \
     --data-urlencode 'ingredients\[3]\[ingredient]=icing sugar'
>> ---
>> + **PHP:**
     >> $curl = curl_init();
curl_setopt_array($curl, array( \
CURLOPT_URL => 'http://localhost/api/v1/get/recipe', \
CURLOPT_RETURNTRANSFER => true, \
CURLOPT_ENCODING => '', \
CURLOPT_MAXREDIRS => 10, \
CURLOPT_TIMEOUT => 0, \
CURLOPT_FOLLOWLOCATION => true, \
CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1, \
CURLOPT_CUSTOMREQUEST => 'POST', \
CURLOPT_POSTFIELDS => 'name=CREAM%20CHEESE%20ICING&cooking_time_in_minutes=10&serves=20&directions%5B0%5D=Mix%20all%20ingredients%20together.&directions%5B1%5D=Enjoy.&ingredients%5B0%5D%5Bmeasure%5D=1%20package&ingredients%5B0%5D%5Bingredient%5D=cream%20cheese&ingredients%5B1%5D%5Bmeasure%5D=1%2F4%20cup&ingredients%5B1%5D%5Bingredient%5D=margarine&ingredients%5B2%5D%5Bmeasure%5D=1%20teaspoon&ingredients%5B2%5D%5Bingredient%5D=vanilla&ingredients%5B3%5D%5Bmeasure%5D=2%20cups&ingredients%5B3%5D%5Bingredient%5D=icing%20sugar', \
CURLOPT_HTTPHEADER => array( \
'Content-Type: application/x-www-form-urlencoded' \
), \
));\
$response = curl_exec($curl); \
curl_close($curl); \
echo $response;

>
> ### Пример ответа:
> ```{"recipe_id":"2"}```
>> ### Пример ответа (дополнительные баллы):
>> ```{"recipe_id":"2"}```