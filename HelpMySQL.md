<h1 align='center'>
${\color{#f5882a}My \color{#2a82f5}SQL🐬 \space \color{#f5452a}Cheat \space Sheet}$
</h1>
<p align='center'>Hoja trampa para filtro o alguna evaluación de MySQL ⚠️SOLAMENTE UTILIZAR CUANDO SEA PERMITIDO⚠️</p>
<p align='center'><b>Si piensa utilizarla en un repositorio ajeno, al menos de créditos :)</b></p>

## ${\color{#f5882a}In \color{#2a82f5}dex}$
- [Creación de BBDD](#crear)
- [CRUD](#crud)
- [Funciones](#funciones)
- [Procedimientos](#procedmientos)
- [Triggers y Events](#trigger_events)
- [Bonus!](#bonus)

<a name="crear"></a>
## ${\color{#f5882a}Creación \space \color{#2a82f5}de \space \color{#f5452a}BBDD}$ 
<p>En este apartado se hará una breve explicación de los pasos fundamentales para la creación de una base de datos en MySQL. Adicionalmente se darán tips para recordar a la hora de crear una.</p>

<li><b>Creación y utilización de base de datos:</b></li>

```sql
CREATE DATABASE NombreBBDD;
USE NombreBBDD;
```

<li><b>Creación de tablas:</b></li>

```sql
CREATE TABLE NombreTabla(
  id int primary key auto_increment not null,
  id_externa int not null,
  for
  nombre varchar(45) not null
-- Agregar más atributos a gusto separados por coma (,)
);
```

<li><b>Creación de usuarios:</b></li>

```sql
CREATE user 'nombre_usuario'@'direccion_ip' IDENTIFIED BY 'contraseña';
```

<a name="crud"></a>
## ${\color{#f5882a}C\color{#2a82f5}R\color{#f5452a}U\color{#f5882a}D}$ 
### En este apartado se hará revisición de los distintos métodos de realizar funciones de CRUD(Create, Read, Update, Delete) dentro de una base de datos.

### ${\color{#358c4c}CREATE}$ 
<li><b>Creación de tablas fue vista en el anterior listado</b></li>
<li><b>Creación Inserción de datos:</b></li>

```sql
INSERT into nombre_tabla(dato1, dato2...) values(valor1, valor2...);
```

### ${\color{#f5882a}READ}$ 
<li><b>Lectura de datos:</b></li>
Una sola tabla

```sql
SELECT * from nombre_tabla where dato1=valor1;
```

Multitabla con join
```sql
SELECT ta1.*
from nombre_tabla ta1
inner join nombre_tabla2 ta2 on ta2.dato1 = ta1.dato1
where dato1=valor1;
```
<p align="center">
<img width=600 src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjqwLKkGPVPwYNfe7ONykAx4hNQ4ELsJI4r8umUbwFKWWUXUGlW8bV74hBoa51ZvddjdgwWRHLRgiH2pTFO3IsP-Z17zUKkzXSSxevM0vrLsxgc6D22VwkUxtAYe782UKWngfVr2doUbjhb/s1600/sql+joins+guide+and+syntax.jpg"></img>
</p>

### ${\color{#2a82f5}UPDATE}$ 
<li><b>Actualizar info de una tabla:</b></li>
⚠️No olvidar el where si solo se va a cambiar un dato en específico⚠️

```sql
UPDATE nombre_tabla set dato2=valor_nuevo where dato1=valor_especifico;
```

### ${\color{#f5452a}DELETE}$ 
<li><b>Borrar info de una tabla:</b></li>
⚠️No olvidar el where si solo se va a borrar un dato en específico⚠️

```sql
DELETE from nombre_tabla where dato1=valor_especifico;
```

<li><b>Borrar TODA la info de una tabla:</b></li>
⚠️No olvidar que LITERALMENTE limpia la tabla⚠️

```sql
TRUNCATE nombre_tabla;
```

<li><b>Borrar una tabla:</b></li>
⚠️No olvidar que borra TODA la tabla incluyendo el contenido⚠️

```sql
DROP table nombre_tabla;
```

<a name="funciones"></a>
## ${\color{#f5882a}Fun\color{#2a82f5}cio\color{#f5452a}nes}$
### Una función es un conjunto de acciones que se realizan una vez llamada.
<li><b>Creación de funciones:</b></li>

```sql
delimiter //
create function nombre_funcion(parametro1 varchar(12), parametro2 int) -- Parámetros deben tener un tipo de dato
returns varchar(255) deterministic -- El tipo de dato que será la respuesta de la ejecución
begin
  -- Proceso que se realiza para mostrar una respuesta
  return "Hello world";
end //
delimiter ;
```
<li><b>Llamar funciones:</b></li>

```sql
select nombre_funcion();
-- En este caso se deja el espacio de parámetros en blanco.
-- Retorna la respuesta: Hello world
```
<p align="center">
<img src="https://i.imgur.com/b4zTkHn.png"></img>
</p>

<li><b>Borrar funciones:</b></li>

```sql
drop function nombre_funcion;
```

<a name="procedmientos"></a>
## ${\color{#f5882a}Proc\color{#2a82f5}edim\color{#f5452a}ientos}$
### Un procedimiento es una serie de pasos que se ejecutan cada que se llama.

<li><b>Creación de procedimientos:</b></li>

```sql
delimiter //
create procedure nombre_procedimiento(in dato1 varchar(100), in dato2 decimal(10,2)) -- "IN" referencia un parametro
                                                                                      -- Puede tener o no(depende)
begin
	-- Proceso que se realiza, ya sea CRUD, etc.
end //
delimiter ;
```

<li><b>Llamar procedimientos:</b></li>
Ejemplo:

```sql
create table tabla1(
	id int auto_increment primary key,
	nombre varchar(20)
);

delimiter //
create procedure nombre_procedimiento()
begin
  insert into tabla1(nombre) values ("Hello world");

end //
delimiter ;
```

```sql
call nombre_procedimiento();
-- En este caso se deja el espacio de parámetros en blanco.
-- Inserta el dato especificado en la tabla

select * from tabla1;
-- Verificar cambios
```
<p align="center">
<img src="https://i.imgur.com/bC0V95b.png"></img>
</p>

<li><b>Borrar procedimientos:</b></li>

```sql
drop procedure nombre_funcion;
```

<a name="trigger_events"></a>
## ${\color{#f5882a}Triggers \space\color{#2a82f5}y \space\color{#f5452a}Events}$

### Un trigger representa un proceso que se realiza antes o después de una determinada acción!
<li><b>Creación de un Trigger:</b></li>

```sql
delimiter //
create trigger nombre_trigger
after delete on city -- Ejecuta luego/antes de acción [CUANDO(before,after)]
for each row
begin
	-- Proceso que se realiza, ya sea CRUD, etc.
end //
delimiter ;
```

### Un evento representa un proceso que se realiza cada cierto tiempo especificado!
<li><b>Creación de un Event:</b></li>

```sql
delimiter //
create event if not exists nombre_evento
on schedule every 1 week -- CADA UNA SEMANA
do
begin
	-- Proceso que se realiza, ya sea CRUD, etc.
end //
delimiter ;
```

<a name="bonus"></a>
## ${\color{#f5882a}Bonus\space\color{#2a82f5}Info}$
<li><b>Recordar hacer USE de la base de datos antes de cualquier cosa.</b></li>
<li><b>Cada linea se debe correr para que se ejecute en el programa.</b></li>
<li><b>Es recomendable que cada uno tenga un identificador único(ID) con AUTO_INCREMENT.</b></li>
