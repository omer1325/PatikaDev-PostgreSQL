# PatikaDev-PostgreSQL

## Ödev 1

**Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.**

```
 SELECT title, description FROM film; 
 ```
 
**Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.**

```
SELECT * FROM film
WHERE length >=60 AND length <= 75; 
```

**Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.**

```
SELECT * FROM film
WHERE (rental_rate = 0.99 AND replacement_cost = 12.99) OR (rental_rate = 0.99 AND replacement_cost = 28.99);
```

**Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?**

```
SELECT last_name FROM customer
WHERE first_name = 'Mary';
```

**Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.*

```
SELECT * FROM film
WHERE length <= 50 AND (rental_rate != 2.99 OR rental_rate != 4.99);
```


## Ödev 2

**Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)**

```
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

**Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)**

```
SELECT first_name, last_name FROM actor
WHERE first_name IN('Penelope', 'Nick', 'Ed');
```

**Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.(IN operatörünü kullanınız.)**

```
SELECT * FROM film
WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
```


## Ödev 3

**Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.**

```
SELECT country FROM country
WHERE country LIKE 'A%a';
```

**Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.**

```
SELECT country FROM country
WHERE LENGTH(country) > 6 AND country LIKE '%n';
```

**Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren**

```
SELECT title FROM film 
WHERE title ILIKE '%t%t%t%t%';
```

**Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.**

```
SELECT * FROM film
WHERE title LIKE 'C%'AND length > 90 AND rental_rate = 2.99;
```


## Ödev 4

**Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.**

```
SELECT DISTINCT replacement_cost FROM film;
```

**Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?**

```
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```

**Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?**

```
SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```
**Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?**

```
SELECT COUNT(*) FROM country
WHERE LENGTH(country) = 5;
```

**City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?**

```
SELECT COUNT(*) FROM city
WHERE city ILIKE '%R';
```


## Ödev 5

**Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.**

```
SELECT title FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```

**Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.**

```
SELECT title FROM film
WHERE title LIKE '%n'
ORDER BY length 
OFFSET 5
LIMIT 5;
```

**Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.**

```
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```


## Ödev 6

**Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?**

```
SELECT AVG(rental_rate) FROM film;
```

**Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?**

```
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';
```

**Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?**

```
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
```

**Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?**

```
SELECT COUNT(DISTINCT(replacement_cost )) FROM film
WHERE length > 150;
```


## Ödev7

**Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.**

```
SELECT rating FROM film
GROUP BY rating;
```

**Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.*

```
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost 
HAVING COUNT(*) > 50;
```

**Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?**

```
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
```

**City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.**

```
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id 
ORDER BY COUNT(*) DESC
LIMIT 1;
```


## Ödev 8

**Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.**

```
CREATE TABLE employee (
	id INTEGER,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
	);
```

**Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.**

```
insert into employee (first_name, last_name, email, birtday) values ('Leandra', 'Shippard', 'lshippard1e@fotki.com', '1983-01-07');
insert into employee (first_name, last_name, email, birtday) values ('Marieann', 'Ricca', 'mricca1f@skyrock.com', '1949-09-06');
insert into employee (first_name, last_name, email, birtday) values ('Vito', 'Gadsdon', 'vgadsdon1g@addtoany.com', '1922-02-09');
insert into employee (first_name, last_name, email, birtday) values ('Nichol', 'Brindle', 'nbrindle1h@wunderground.com', '1969-01-22');
insert into employee (first_name, last_name, email, birtday) values ('Hank', 'Garlant', 'hgarlant1i@dell.com', '1964-04-23');
insert into employee (first_name, last_name, email, birtday) values ('Huey', 'Stapforth', 'hstapforth1j@blogspot.com', '1908-04-20');
insert into employee (first_name, last_name, email, birtday) values ('Dulcea', 'Odd', 'dodd1k@wikia.com', '1968-08-19');
insert into employee (first_name, last_name, email, birtday) values ('Kathlin', 'Garfoot', 'kgarfoot1l@live.com', '1989-12-11');
insert into employee (first_name, last_name, email, birtday) values ('Lesya', 'Wickins', 'lwickins1m@bizjournals.com', '1926-08-19');
insert into employee (first_name, last_name, email, birtday) values ('Umeko', 'Wayper', 'uwayper1n@answers.com', '1948-08-20');
insert into employee (first_name, last_name, email, birtday) values ('Brooks', 'Lefort', 'blefort1o@deliciousdays.com', '1987-04-28');
insert into employee (first_name, last_name, email, birtday) values ('Reeta', 'Coch', 'rcoch1p@blogger.com', '1923-12-02');
insert into employee (first_name, last_name, email, birtday) values ('Elisabetta', 'Snaden', 'esnaden1q@independent.co.uk', '1982-07-23');
insert into employee (first_name, last_name, email, birtday) values ('Letitia', 'Stirrup', 'lstirrup1r@prweb.com', '1989-04-11');
insert into employee (first_name, last_name, email, birtday) values ('Daniella', 'Rendle', 'drendle1s@abc.net.au', '1932-10-23');
insert into employee (first_name, last_name, email, birtday) values ('Gray', 'Danzey', 'gdanzey1t@elpais.com', '1924-10-16');
insert into employee (first_name, last_name, email, birtday) values ('Sherlock', 'Rossiter', 'srossiter1u@marketwatch.com', '1975-04-03');
insert into employee (first_name, last_name, email, birtday) values ('Carina', 'Siemens', 'csiemens1v@etsy.com', '1906-07-18');
insert into employee (first_name, last_name, email, birtday) values ('Adiana', 'Brand-Hardy', 'abrandhardy1w@arizona.edu', '1946-09-14');
insert into employee (first_name, last_name, email, birtday) values ('Rene', 'Witchell', 'rwitchell1x@prnewswire.com', '1962-03-04');
insert into employee (first_name, last_name, email, birtday) values ('Kaela', 'Withringten', 'kwithringten1y@china.com.cn', '1946-12-25');
insert into employee (first_name, last_name, email, birtday) values ('Alberta', 'McClinton', 'amcclinton1z@google.es', '1930-06-24');
insert into employee (first_name, last_name, email, birtday) values ('Lockwood', 'Labb', 'llabb20@w3.org', '1989-06-19');
insert into employee (first_name, last_name, email, birtday) values ('Tarah', 'Hubbart', 'thubbart21@gizmodo.com', '1956-12-23');
insert into employee (first_name, last_name, email, birtday) values ('Renee', 'Haspineall', 'rhaspineall22@topsy.com', '1972-02-10');
insert into employee (first_name, last_name, email, birtday) values ('Veda', 'Strowther', 'vstrowther23@123-reg.co.uk', '1998-07-21');
insert into employee (first_name, last_name, email, birtday) values ('Jenifer', 'Schoales', 'jschoales24@ca.gov', '1957-09-10');
insert into employee (first_name, last_name, email, birtday) values ('Ritchie', 'Chattey', 'rchattey25@etsy.com', '1961-08-20');
insert into employee (first_name, last_name, email, birtday) values ('Christoph', 'D''Elias', 'cdelias26@geocities.com', '1942-04-28');
insert into employee (first_name, last_name, email, birtday) values ('Prissie', 'Keeton', 'pkeeton27@cocolog-nifty.com', '1901-04-14');
insert into employee (first_name, last_name, email, birtday) values ('Tamara', 'Ebbings', 'tebbings28@symantec.com', '1940-09-04');
insert into employee (first_name, last_name, email, birtday) values ('Parry', 'Scohier', 'pscohier29@mac.com', '1947-04-04');
insert into employee (first_name, last_name, email, birtday) values ('Britta', 'Drawmer', 'bdrawmer2a@mysql.com', '1936-12-21');
insert into employee (first_name, last_name, email, birtday) values ('Gina', 'Winder', 'gwinder2b@timesonline.co.uk', '1958-10-21');
insert into employee (first_name, last_name, email, birtday) values ('Danika', 'Ratnege', 'dratnege2c@yahoo.co.jp', '1962-12-01');
insert into employee (first_name, last_name, email, birtday) values ('Hurlee', 'Symper', 'hsymper2d@spiegel.de', '1917-11-16');
insert into employee (first_name, last_name, email, birtday) values ('Si', 'Sliman', 'ssliman2e@sciencedirect.com', '1907-05-19');
insert into employee (first_name, last_name, email, birtday) values ('Franklyn', 'Vogt', 'fvogt2f@quantcast.com', '1926-06-21');
insert into employee (first_name, last_name, email, birtday) values ('Meghan', 'Crann', 'mcrann2g@goo.gl', '1901-10-09');
insert into employee (first_name, last_name, email, birtday) values ('Donna', 'Coutts', 'dcoutts2h@woothemes.com', '1936-10-06');
insert into employee (first_name, last_name, email, birtday) values ('Tabitha', 'Grigolli', 'tgrigolli2i@buzzfeed.com', '1943-08-08');
insert into employee (first_name, last_name, email, birtday) values ('Lindsay', 'Smorthwaite', 'lsmorthwaite2j@sitemeter.com', '1923-11-02');
insert into employee (first_name, last_name, email, birtday) values ('Chicky', 'Giabucci', 'cgiabucci2k@mozilla.org', '1959-03-17');
insert into employee (first_name, last_name, email, birtday) values ('Caresse', 'MacCorley', 'cmaccorley2l@storify.com', '1985-03-06');
insert into employee (first_name, last_name, email, birtday) values ('Emmanuel', 'Guitel', 'eguitel2m@cbslocal.com', '1993-01-12');
insert into employee (first_name, last_name, email, birtday) values ('Dagmar', 'Storton', 'dstorton2n@kickstarter.com', '1982-05-02');
insert into employee (first_name, last_name, email, birtday) values ('Rosamond', 'Hatterslay', 'rhatterslay2o@people.com.cn', '1978-12-10');
insert into employee (first_name, last_name, email, birtday) values ('Ambrose', 'Belle', 'abelle2p@blogs.com', '1972-11-06');
insert into employee (first_name, last_name, email, birtday) values ('Noe', 'Pietroni', 'npietroni2q@microsoft.com', '1938-03-12');
insert into employee (first_name, last_name, email, birtday) values ('Lucine', 'Corbould', 'lcorbould2r@live.com', '1937-09-11');
```

**Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.**

```
UPDATE employee SET name = 'Ambrose' WHERE id = 50;
UPDATE employee SET email = 'abelle2p@blogs.com' WHERE name = 'Ambrose';
UPDATE employee SET birthday = '2021/11/29' WHERE email = 'lcorbould2r@live.com';
UPDATE employee SET birthday = '2021/05/29',name = 'Dagmar' WHERE email = 'lcorbould2r@live.com';
UPDATE employee SET name = 'Ambrose',birthday = '2021/05/03' WHERE id = 1;
```

**Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.**

```
DELETE FROM employee WHERE id = '49';
DELETE FROM employee WHERE email = 'npietroni2q@microsoft.com';
DELETE FROM employee WHERE birthday = '2021/05/03';
DELETE FROM employee WHERE name = 'Ömer';
DELETE FROM employee WHERE id = '50';
```


## Ödev 9

**City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.**

```
SELECT city, country FROM city
JOIN country ON (country.id = city.country_id );
```

**Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.**

```
SELECT payment_id, first_name , last_name FROM customer
JOIN payment ON (payment.customer_id = customer.id);
```

**Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.**

```
SELECT first_name,last_name,rental_id FROM customer 
INNER JOIN rental ON( customer.id = rental.customer_id );
```


## Ödev 10

**City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.**

```
SELECT city, country FROM city 
LEFT JOIN country ON(city.country_id = countryid );
```

**Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.**

```
SELECT first_name, last_name FROM customer 
LEFT JOIN payment ON(payment.customer_id = customer.id );
```

**Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.**

```
SELECT first_name, last_name FROM customer 
FULL JOIN rental ON(rental.customer_id = customer.id );
```


## Ödev 11

**Actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.**

```
(
SELECT first_name FROM actor
)
UNION
(
SELECT first_name FROM customer
);
```

**Actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.**

```
(
SELECT first_name FROM actor
)
INTERSECT
(
SELECT first_name FROM customer
);
```

**Actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.**

```
(
SELECT first_name FROM actor
)
EXCEPT
(
SELECT first_name FROM customer
);
```

**İlk 3 sorguyu tekrar eden veriler için de yapalım.**

```
( 
SELECT first_name FROM actor 
)
UNION ALL
( 
SELECT first_name FROM customer 
);
```

```
( 
SELECT first_name FROM actor 
)
INTERSECT ALL
( 
SELECT first_name FROM customer 
);
```

```
( 
SELECT first_name FROM actor 
)
EXCEPT ALL
( 
SELECT first_name FROM customer 
);
```


## Ödev 12

**Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?**

```
SELECT COUNT(*) FROM film
WHERE length > 
(
  SELECT AVG(length) FROM film
);
```

**Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?**

```
SELECT COUNT(*) FROM film
WHERE rental_rate =
(
  SELECT MAX(rental_rate) FROM film
);
```

**Film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.**

```
SELECT title FROM film
WHERE film_id = ANY
( 
  SELECT film_id FROM film
  WHERE rental_rate = 
  ( 
    SELECT MIN(rental_rate ) FROM film 
  )
  AND
  replacement_cost = 
  ( 
    SELECT MIN(replacement_cost) FROM film 
  ) 
);
```

**Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.**

```
SELECT first_name, last_name FROM customer
INNER JOIN payment ON (customer.id = payment.customer_id)
WHERE amount = 
( 
  SELECT MAX(amount) from payment 
);
```









