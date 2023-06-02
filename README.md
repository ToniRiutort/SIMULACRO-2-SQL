# SIMULACRO-2-SQL
## Enunciados
1. Muestra el título del libro que se pretó por primera vez hace más tiempo.
2. Muestra los libros que se ham prestado al menos una vez, pero no en los últimos seis meses.
3. Muestra el mes con el mayor número de préstamos.
4. Muestra los autores cuyos libros se prestan en promedio menos de 3 veces.
5. Muestra todos los préstamos que aún no han sido devueltos.
6. Muestra el título de los libros que fueron prestados en el ñultimo mes.
7. Muestra el autor que tiene más libros en la biblioteca.
8. Muestra el título del libro que se ha prestado más veces.
9. Muestra los libros que nunca se han prestado.
10. Muestra el año con la mayor cantidad de préstamos.
## Tablas
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/d241815a-e590-451f-875a-97d4716276cc)
## Soluciones
1. SELECT titulo FROM `libros` ORDER BY anio_publicacion ASC LIMIT 1;
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/dfe31080-166c-44f6-8799-10d15e2f8ffd)
2. SELECT titulo FROM `libros` INNER JOIN prestamos ON libros.id_libro = prestamos.id_libro WHERE prestamos.fecha_prestamo < NOW() - INTERVAL 6 MONTH;
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/72c160f1-5d6d-4acc-af1e-9faf0d6c409d)
3. SELECT COUNT(fecha_prestamo), fecha_prestamo FROM `prestamos` GROUP BY MONTH(fecha_prestamo) ORDER BY COUNT(fecha_prestamo) DESC LIMIT 2; El limite 2 para demostrar que hay más de uno con el mismo valor.
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/2bda121f-5b03-4bdf-bdda-e204c775279e)
4. SELECT autor, COUNT(prestamos.id_libro) FROM `libros` INNER JOIN prestamos ON libros.id_libro = prestamos.id_libro GROUP BY prestamos.id_libro HAVING COUNT(prestamos.id_libro)<3;
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/c56461d5-0682-477d-8f51-23991276c0cc)
5. SELECT id_prestamo FROM `prestamos` WHERE fecha_prestamo = NULL;
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/26cabffb-91ea-47fb-aae3-bb2b222d8886)
6. SELECT titulo FROM `libros` INNER JOIN prestamos ON libros.id_libro = prestamos.id_libro WHERE prestamos.fecha_prestamo> NOW() - INTERVAL 1 MONTH;
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/6f07e13b-a5c6-4761-b230-77fe1c2e7a9d)
7. SELECT COUNT(autor), autor FROM `libros` GROUP BY autor ORDER BY COUNT(autor) DESC LIMIT 2; El limite 2 para demostrar que hay más de uno con el mismo valor.
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/711f9e29-6ff6-4ebb-976a-b5278f5d256d)
8. SELECT titulo FROM `libros` INNER JOIN prestamos ON libros.id_libro = prestamos.id_libro GROUP BY prestamos.id_libro ORDER BY COUNT(prestamos.id_libro) DESC LIMIT 2; El limite 2 para demostrar que hay más de uno con el mismo valor.
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/7507d645-470b-4363-8e58-a94aa917913b)
9. SELECT titulo FROM `libros` RIGHT JOIN prestamos ON libros.id_libro = prestamos.id_libro WHERE prestamos.fecha_prestamo = NULL;
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/b41df5a1-797b-408e-8277-b2d5688852fa)
10. SELECT COUNT(fecha_prestamo),YEAR(fecha_prestamo) FROM `prestamos` GROUP BY YEAR(fecha_prestamo) ORDER BY COUNT(fecha_prestamo) DESC LIMIT 1;
![image](https://github.com/ToniRiutort/SIMULACRO-2-SQL/assets/104781981/f620e628-776f-4272-a63f-39d4b0cb8a26)
