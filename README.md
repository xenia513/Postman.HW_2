## Postman.HW_2

### Homework to the second Postman lesson - Vadim Ksendzov's course

#### 1

http://162.55.220.72:5005/first
1. Отправить запрос.
2. Статус-код 200.

        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });

3. Проверить, что в *body* приходит правильный *string*.

        pm.test("Body matches string", function () {
            pm.expect(pm.response.text()).to.include("This is the first responce from server!ss");
        });
___

#### 2

http://162.55.220.72:5005/user_info_3
1. Отправить запрос.
2. Статус-код 200.

        pm.test("Status code is 200", function () { 
            pm.response.to.have.status(200);
        });

3. Спарсить *response body* в *json*.

        var jsonResponse = pm.response.json(); 

4. Проверить, что *name* в ответе равно *name* в **request** (*name* вбить руками).

        pm.test("Name is correct", function () { 
            pm.expect(jsonResponse.name).to.eql("doshik");    
        });

5. Проверить, что *age* в ответе равно *age* в **request** (*age* вбить руками).

        pm.test("Age is correct", function () {
            pm.expect(jsonResponse.age).to.eql("48");    
        });

6. Проверить, что *salary* в ответе равно *salary* в **request** (*salary* вбить руками).

        pm.test("Salary is correct", function () {
            pm.expect(jsonResponse.salary).to.eql(100000);    
        })

7. Спарсить *request*.

        var Request = pm.request.body.formdata;

8. Проверить, что *name* в ответе равно *name* в **request** (*name* забрать из **request**).

        pm.test("Name is correct_2", function () {
            pm.expect(jsonResponse.name).to.eql(Request.get("name"));    
        });

9. Проверить, что *age* в ответе равно *age* в **request** (*age* забрать из **request**).

        pm.test("Age is correct_2", function () {
            pm.expect(jsonResponse.age).to.eql(Request.get("age"));    
        });

10. Проверить, что *salary* в ответе равно *salary* в **request** (*salary* забрать из **request**).

        pm.test("Salary is correct_2", function () {
            pm.expect(jsonResponse.salary).to.eql(+Request.get("salary"));       
        }); 

11. Вывести в консоль параметр *family* из **response**.

        console.log(jsonResponse.family)

12. Проверить что *u_salary_1_5_year* в ответе равно *salary\*4* (*salary* забрать из **request**).

        pm.test("Salary_1_5_year is correct", function () {
            pm.expect(jsonResponse.family.u_salary_1_5_year).to.eql(Request.get("salary")*4);         
        }); 
___

#### 3
http://162.55.220.72:5005/object_info_3
1. Отправить запрос.
2. Статус-код 200.

        pm.test("Status code is 200", function () { 
            pm.response.to.have.status(200);
        });

3. Спарсить *response body* в *json*.

        var jsonResponse = pm.response.json(); 

4. Спарсить **request**.

        var Request = pm.request.url.query;

5. Проверить, что *name* в ответе равно *name* в **request** (*name* забрать из **request**).

        pm.test("Name is correct", function () {
            pm.expect(jsonResponse.name).to.eql(Request.get("name"));    
        });

6. Проверить, что *age* в ответе равно *age* в **request** (*age* забрать из **request**).

        pm.test("Age is correct", function () {
            pm.expect(jsonResponse.age).to.eql(Request.get("age"));      
        });

7. Проверить, что *salary* в ответе равно *salary* в **request** (*salary* забрать из **request**).

        pm.test("Salary is correct", function () {
            pm.expect(jsonResponse.salary).to.eql(+Request.get("salary"));          
        }); 

8. Вывести в консоль параметр *family* из **response**.

        console.log(jsonResponse.family)

9. Проверить, что у параметра *dog* есть параметр *name*.

        pm.test("dog has name", function () {
           pm.expect(jsonResponse.family.pets.dog).property("name");         
        }); 

10. Проверить, что у параметра *dog* есть параметр *age*.

        pm.test("dog has age", function () {
           pm.expect(jsonResponse.family.pets.dog).property("age");         
        }); 

11. Проверить, что параметр *name* имеет значение `Luky`.

        pm.test("dog's name is correct", function () {
           pm.expect(jsonResponse.family.pets.dog.name).to.eql("Luky");         
        }); 

12. Проверить, что параметр *age* имеет значение `4`.

        pm.test("dog's age is correct", function () {
           pm.expect(jsonResponse.family.pets.dog.age).to.eql(4);         
        }); 
___

#### 4
http://162.55.220.72:5005/object_info_4
1. Отправить запрос.
2. Статус-код 200.

        pm.test("Status code is 200", function () { 
            pm.response.to.have.status(200);
        });

3. Спарсить *response body* в *json*.

        var Response = pm.response.json(); 

4. Спарсить **request**.

        var Request = pm.request.url.query;

5. Проверить, что *name* в ответе равно *name* в **request** (*name* забрать из **request**).

        pm.test("Name is correct", function () {
            pm.expect(Response.name).to.eql(Request.get("name"));    
        });

6. Проверить, что *age* в ответе равно *age* из **request** (*age* забрать из **request**).

        pm.test("Age is correct", function () {
            pm.expect(Response.age).to.eql(+Request.get("age"));      
        });

7. Вывести в консоль параметр *salary* из **request**.

        console.log(Request.get("salary"));  

8. Вывести в консоль параметр *salary* из **response**.

        console.log(Response.salary);  

9. Вывести в консоль 0-й элемент параметра *salary* из **response**.

        console.log(Response.salary[0]);  

10. Вывести в консоль 1-й элемент параметра *salary* параметр *salary* из **response**.

        console.log(Response.salary[1]); 

11. Вывести в консоль 2-й элемент параметра *salary* параметр *salary* из **response**.

        console.log(Response.salary[2]); 

12. Проверить, что 0-й элемент параметра *salary* равен *salary* из **request** (*salary* забрать из **request**).

        pm.test("salary0 is correct", function () {
           pm.expect(Response.salary[0]).eql(+Request.get("salary"));           
        }); 

13. Проверить, что 1-й элемент параметра *salary* равен *salary\*2* из **request** (*salary* забрать из **request**).

        pm.test("salary1 is correct", function () {
           pm.expect(Response.salary[1]).eql+(Request.get("salary")*2);        
        }); 

14. Проверить, что 2-й элемент параметра *salary* равен *salary\*3* из **request** (*salary* забрать из **request**).

        pm.test("salary2 is correct", function () {
           pm.expect(Response.salary[2]).eql+(Request.get("salary")*3);        
        });


15. Создать в окружении переменную *name*.
18. Передать в окружение переменную *name*.

        pm.environment.set("name", (Request.get("name")));

16. Создать в окружении переменную *age*.
19. Передать в окружение переменную *age*.

        pm.environment.set("age", (Request.get("age")));

17. Создать в окружении переменную *salary*.
20. Передать в окружение переменную *salary*.

        pm.environment.set("salary", (Request.get("salary")));

21. Написать цикл, который выведет в консоль по порядку элементы списка из параметра *salary*.

        Response.salary.forEach(element=>console.log(element));

___

#### 5
http://162.55.220.72:5005/user_info_2
1. Вставить параметр *salary* из окружения в **request**.
2. Вставить параметр *age* из окружения в *age*.
3. Вставить параметр *name* из окружения в *name*.

Указанные параметры вносим в *body* запроса в формате form-data, в значении указываем переменную, созданную в окружении в предыдущем задании

![Вставляем параметр из окружения](https://github.com/xenia513/Postman.HW_2/assets/109612371/52669054-1b34-4fd0-af2e-53b6603145fd)

4. Отправить запрос.
5. Статус-код 200.

        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });

        6. Спарсить *response body* в *json*.

        var Response = pm.response.json();

7. Спарсить **request**.

        var Request = pm.request.body.formdata;

8. Проверить, что **json response** имеет параметр *start_qa_salary*.

        pm.test("has start_qa_salary", function () {
            pm.expect(Response).property("start_qa_salary");
        });

9. Проверить, что **json response** имеет параметр *qa_salary_after_6_months*.

        pm.test("has qa_salary_after_6_months", function () {
            pm.expect(Response).property("qa_salary_after_6_months");
        });

10. Проверить, что **json response** имеет параметр *qa_salary_after_12_months*.

        pm.test("has qa_salary_after_12_months", function () {
            pm.expect(Response).property("qa_salary_after_12_months");
        });

11. Проверить, что **json response** имеет параметр *qa_salary_after_1.5_year*.

        pm.test("has qa_salary_after_1.5_months", function () {
            pm.expect(Response).property("qa_salary_after_1.5_year");
        });

12. Проверить, что **json response** имеет параметр *qa_salary_after_3.5_years*.

        pm.test("has qa_salary_after_3.5_months", function () {
            pm.expect(Response).property("qa_salary_after_3.5_years");
        });

13. Проверить, что **json response** имеет параметр *person*.

        pm.test("has person", function () {
            pm.expect(Response).property("person");
        });

14. Проверить, что параметр *start_qa_salary* равен *salary* из **request** (*salary* забрать из **request**).

        pm.test("start_qa_salary is correct", function () {
            pm.expect(Response.start_qa_salary).to.eql(+Request.get("salary"));
        });

15. Проверить, что параметр *qa_salary_after_6_months* равен *salary\*2* из **request** (*salary* забрать из **request**).

        pm.test("qa_salary_after_6_months is correct", function () {
            pm.expect(Response.qa_salary_after_6_months).to.eql(Request.get("salary")*2);  
        });

16. Проверить, что параметр *qa_salary_after_12_months* равен *salary\*2.7* из **request** (*salary* забрать из **request**).

        pm.test("qa_salary_after_12_months is correct", function () {
            pm.expect(Response.qa_salary_after_12_months).to.eql(Request.get("salary")*2.7);  
        });

17. Проверить, что параметр *qa_salary_after_1.5_year* равен *salary\*3.3* из **request** (*salary* забрать из **request**).

        pm.test("qa_salary_after_1.5_months is correct", function () {
            pm.expect(Response["qa_salary_after_1.5_year"]).to.eql(Request.get("salary")*3.3);
        });

18. Проверить, что параметр *qa_salary_after_3.5_years* равен *salary\*3.8* из **request** (*salary* забрать из **request**).

        pm.test("qa_salary_after_3.5_months is correct", function () {
            pm.expect(Response["qa_salary_after_3.5_years"]).to.eql(Request.get("salary")*3.8);
        });

19. Проверить, что в параметре *person* 1-й элемент из *u_name* равен *salary* из **request** (*salary* забрать из **request**).

        pm.test("u_name1 is correct", function () {
            pm.expect(Response.person.u_name[1]).to.eql+(Request.get("salary"));  
        });

20. Проверить, что что параметр *u_age* равен *age* из **request** (*age* забрать из **request**).

        pm.test("u_age is correct", function () {
           pm.expect(Response.person.u_name[2]).to.eql+(Request.get("age"));           
        }); 

21. Проверить, что параметр *u_salary_5_years* равен *salary\*4.2* из **request** (*salary* забрать из **request**).

        pm.test("u_salary_5_years is correct", function () {
           pm.expect(Response.person.u_salary_5_years).to.eql(Request.get("salary")*4.2);           
            }); 

22. \*\*\*Написать цикл, который выведет в консоль по порядку элементы списка из параметра *person*.

        Object.keys(pm.response.json().person).forEach(element => console.log(element));
