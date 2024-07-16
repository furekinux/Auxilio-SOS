<h1 align='center'>
${\color{#f5882a}My \color{#2a82f5}SQL🐬 \space \color{#f5452a}Cheat \space Sheet}$
</h1>
<p align='center'>Hoja trampa para filtro de MySQL, ⚠️SOLAMENTE UTILIZAR CUANDO SEA PERMITIDO⚠️</p>
<p align='center'><b>Si piensa utilizarla en un repositorio ajeno, al menos de créditos :)</b></p>

## ${\color{#f5882a}In \color{#2a82f5}dex}$
- [Creación de BBDD](#crear)
- [CRUD](#crud)

## ${\color{#f5882a}Creación \space \color{#2a82f5}de \space \color{#f5452a}BBDD}$ <a name="crear"></a>
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
  nombre varchar(45) not null
-- Agregar más atributos a gusto separados por coma (,)
);
```

<li><b>Creación de usuarios</b></li>

```sql
CREATE user 'nombre_usuario'@'direccion_ip' IDENTIFIED BY 'contraseña';
```

## ${\color{#f5882a}C\color{#2a82f5}R\color{#f5452a}U\color{#f5882a}D}$ <a name="crud"></a>



## ${\color{#f5882a}Triggers \space\color{#2a82f5}y \space\color{#f5452a}Events}$ <a name="trieve"></a>
