# Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

## Ödev 1

* film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
```
SELECT title, description FROM film;
```
* film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
```
SELECT * FROM film WHERE length > 60 AND length < 75;
```
* film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
```
SELECT * FROM film WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
```
* customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
```
SELECT last_name FROM customer WHERE first_name = 'Mary';
```
* film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
```
SELECT * FROM film WHERE length <= 50 AND rental_rate NOT IN (2.99, 4.99);
```

## Ödev 2

* film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
```
SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```
* .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
```
SELECT first_name, last_name FROM actor WHERE first_name IN ('Penelope', 'Nick', 'Ed');
```
* film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
```
SELECT * FROM film WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
```

## Ödev 3

* country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
```
SELECT * FROM country WHERE country LIKE 'A%a';
```
* country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```
SELECT * FROM country WHERE LENGTH(country) >= 6 AND country LIKE '%n';
```
* film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
```
SELECT * FROM film WHERE title ILIKE '%T%T%T%T%';
```
* film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
```
SELECT * FROM film WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
```

## Ödev 4

* film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
```
SELECT DISTINCT replacement_cost FROM film;
```
* film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
```
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```
* film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```
SELECT COUNT(*) FROM film WHERE title LIKE 'T%' AND rating = 'G';
```
* country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```
SELECT COUNT(*) FROM country WHERE LENGTH(country) = 5;
```
* city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
```
SELECT COUNT(*) FROM city WHERE city ILIKE '%r';
```

## Ödev 5

* film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```
SELECT title, length FROM film WHERE title LIKE '%n' ORDER BY length DESC LIMIT 5;
```
* film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
```
SELECT title, length FROM film WHERE title LIKE '%n' ORDER BY length ASC OFFSET 5 LIMIT 5;
```
* customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```
SELECT * FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;
```

## Ödev 6

* film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```
SELECT AVG(rental_rate) AS ort FROM film;
```
* film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
```
SELECT COUNT(*) AS c_title FROM film WHERE title LIKE 'C%';
```
* film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```
SELECT MAX(length) AS length_movie FROM film WHERE rental_rate = 0.99;
```
* film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```
SELECT COUNT(DISTINCT replacement_cost) FROM film WHERE length > 150;
```

## Ödev 7

* film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```
SELECT rating, COUNT(*) AS film_sayisi FROM film GROUP BY rating;
```
* film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```
SELECT replacement_cost, COUNT(*) AS film_sayisi FROM film GROUP BY replacement_cost HAVING COUNT(*) > 50;
```
* customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
```
SELECT store_id, COUNT(*) AS musteri_sayisi FROM customer GROUP BY store_id;
```
* city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
```
SELECT country_id, COUNT(*) AS sehir_sayisi FROM city GROUP BY country_id ORDER BY sehir_sayisi DESC LIMIT 1;
```

## Ödev 8

* test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```
CREATE TABLE employee (
  id INTEGER,
  name VARCHAR(50),
  birthday DATE,
  email VARCHAR(100)
);
```
* Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
```
INSERT INTO employee (id, name, birthday, email)
VALUES
  (1, 'John Doe', '1990-05-15', 'john.doe@example.com'),
  (2, 'Jane Smith', '1988-12-03', 'jane.smith@example.com'),
  ...
  ;
```
* Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```
UPDATE employee SET name = 'John Johnson' WHERE id = 1;
UPDATE employee SET birthday = '1990-01-20' WHERE name = 'Jane Smith';
UPDATE employee SET name = 'Jane Emily' WHERE id = 2;
UPDATE employee SET birthday = '1990-01-20' WHERE name = 'John Doe';
UPDATE employee SET email = 'john_doe@example.com' WHERE name = 'John Doe';
```
* Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```
DELETE FROM employee WHERE id = 1;
DELETE FROM employee WHERE name = 'Jane Smith';
DELETE FROM employee WHERE email = 'jane.smith@example.com';
DELETE FROM employee WHERE birthday = '1988-12-03';
```

## Ödev 9

* city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
SELECT city, country FROM city INNER JOIN country ON city.country_id = country.country_id;
```
* customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
SELECT payment_id, first_name, last_name FROM customer INNER JOIN payment ON customer.customer_id = payment.customer_id;
```
* customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
SELECT rental_id, first_name, last_name FROM customer INNER JOIN rental ON customer.customer_id = rental.customer_id;
```

## Ödev 10

* city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
```
SELECT city, country FROM city LEFT JOIN country ON city.country_id = country.country_id;
```
* customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
```
SELECT payment_id, first_name, last_name FROM customer RIGHT JOIN payment ON customer.customer_id = payment.customer_id;
```
* customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
```
SELECT rental_id, first_name, last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;
```
