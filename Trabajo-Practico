use master
go
create database TPBD
go

create table PERSONAL_MEDICO1(
id_medico int not null identity (1,1) check (id_medico > = 0 and id_medico <= 9999 ),
nombre varchar(30) not null,
profesion varchar(30) not null check (profesion in ('Medico General', 'Medico Especialista', 'Enfermera')),
genero char(1) not null check (genero in('M','F','N')),
fecha_incorporacion date not null,

constraint pk_personal_medico1 PRIMARY KEY (id_medico),
);

create table PACIENTES1(
id_paciente int not null identity (1,1) check (id_paciente > = 0 and id_paciente <= 9999 ),
nombre varchar(30) not null,
edad int not null check(edad > = 0 and edad <= 100),
nss varchar(40) not null UNIQUE,
direccion varchar(40) not null,
telefono varchar(10) not null,
telefono_celular int,
email varchar(30),
genero char(1) not null check (genero in('M','F','N')),

constraint pk_pacientes1 PRIMARY KEY (id_paciente),
);

create table CONSULTA1(
id_medico int not null,
id_paciente int not null,
fecha date not null,
comentarios varchar(100),
id_consulta int not null identity(1,1),

constraint pk_consulta1 primary key(id_consulta),
constraint fk_consulta_medico1 foreign key (id_medico) references PERSONAL_MEDICO1(id_medico),
constraint fk_consulta_pacientes1 foreign key (id_paciente) references PACIENTES1(id_paciente),
);


create table RECETA1(
id_consulta int not null,
marca varchar(30) not null,
comentarios varchar(100),
fecha_receta date not null,

constraint fk_receta_consulta1 foreign key (id_consulta) references CONSULTA1(id_consulta),
);


/** CREAR DATOS PARA CADA TABLA**/

create procedure crearPersonalMedico
@medico_nombre varchar(30),
@medico_profesion varchar(30),
@medico_genero char(1),
@medico_fecha_incorporacion date
as
insert into PERSONAL_MEDICO1 values (@medico_nombre,@medico_profesion,@medico_genero,@medico_fecha_incorporacion)
go

EXEC crearPersonalMedico 'Adonys', 'Medico General', 'M', '2023-04-02'
EXEC crearPersonalMedico 'Julieta', 'Enfermera', 'F', '2021-04-02'
EXEC crearPersonalMedico 'Tomas', 'Medico especialista', 'M', '2017-04-02'
EXEC crearPersonalMedico 'Mirta', 'Enfermera', 'F', '2013-04-02'
EXEC crearPersonalMedico 'Gisell', 'Medico General', 'F', '2023-04-02'
EXEC crearPersonalMedico 'Leandro', 'Medico General', 'M', '2023-04-02'
EXEC crearPersonalMedico 'Sandra', 'Medico especialista', 'F', '2023-04-02'
EXEC crearPersonalMedico 'Diana', 'Enfermera', 'F', '2020-07-08'
EXEC crearPersonalMedico 'Maria', 'Medico especialista', 'F', '2005-07-08'

update PERSONAL_MEDICO1
set profesion = 'Medico especialista'
where id_medico = 9


select * from PERSONAL_MEDICO1


create procedure crearPaciente
@paciente_nombre varchar(30),
@paciente_edad int,
@paciente_nss varchar(40),
@paciente_direccion varchar(40),
@paciente_telefono varchar(10),
@paciente_telefono_celular int,
@paciente_email varchar(30),
@paciente_genero char(1)
as
insert into PACIENTES1 values (@paciente_nombre, @paciente_edad, @paciente_nss, @paciente_direccion, @paciente_telefono, @paciente_telefono_celular, @paciente_email, @paciente_genero)
go

exec crearPaciente 'Ana','20','1234','Avellaneda','3456785','1234567890','ana@gmail.com','F'
exec crearPaciente 'Ramiro','40','4567','Rivadavia','3456785','1234567890','Ramiro@gmail.com','M'
exec crearPaciente 'Fabricio','23','8901','Avenida Reforma','3456785','1234567890','Julian@gmail.com','M'
exec crearPaciente 'Laura','54','9876','Ramon Falcon','3456785','1234567890','Laura@gmail.com','F'
exec crearPaciente 'Nicolas','20','5432','Avellaneda','3456785','1234567890','Nicolas@gmail.com','M'
exec crearPaciente 'Claudia','13','8356','Avellaneda','3456785','1234567890','Claudia@gmail.com','M'
exec crearPaciente 'Gaston','48','5555','Avellaneda','3456785','1234567890','Gaston@gmail.com','M'
exec crearPaciente 'Jessica','30','4444','Avellaneda','3456785','1234567890','Jessica@gmail.com','F'
exec crearPaciente 'Graciela','63','2222','Palermo','3456785','1234567890','Graciela@gmail.com','F'
exec crearPaciente 'Ricardo','70','1111','Caballito','3456785','1234567890','Ricardo@gmail.com','M'
exec crearPaciente 'Santiago','19','6666','Almagro','3456785','1234567890','Santiago@gmail.com','M'

select * from PACIENTES1





create procedure crearConsulta
@id_medico int,
@id_paciente int,
@consulta_fecha date,
@consulta_comentarios varchar(100)
as
insert into CONSULTA1 values (@id_medico, @id_paciente, @consulta_fecha, @consulta_comentarios)
go

exec crearConsulta 4,1,'2023','consulta de control'
exec crearConsulta 2,3,'2020','consulta de control'
exec crearConsulta 1,4,'2022','consulta de control'
exec crearConsulta 3,2,'2021','consulta de control'
exec crearConsulta 2,5,'2005','consulta de control'
exec crearConsulta 5,1,'2020','consulta de control'
exec crearConsulta 3,8,'2022','consulta de control'
exec crearConsulta 7,9,'2021','consulta de control'
exec crearConsulta 5,10,'2018','consulta de control'



select * from CONSULTA1


create procedure crearReceta
@id_consulta int,
@receta_marca varchar(30),
@receta_comentarios varchar(100),
@fecha_receta date
as
insert into RECETA1 values (@id_consulta, @receta_marca, @receta_comentarios,@fecha_receta)
go

exec crearReceta 3,'Paracetamol','tomar cada 8 hrs','2023'
exec crearReceta 5,'Ibuprofeno','tomar cada 3 hrs','2023'
exec crearReceta 4,'Paracetamol','tomar cada 9 hrs','2023'
exec crearReceta 1,'Ibuprofeno','tomar cada 8 hrs','2023'
select * from RECETA1




/**1.Crear un procedimiento almacenado que permita la carga por parámetros de cada uno de los objetos de datos definidos
(médicos, pacientes, consultas, recetas, entre otros)**/




/**
5. Mostrar el nombre y nº de la seguridad social de los pacientes que aún no han hecho ni una sola consulta.**/

select nombre, nss
from PACIENTES1 
where id_paciente not in (select id_paciente from CONSULTA1)




/**
6. Mostrar el nombre de los profesionales Médicos que han tenido consulta con él paciente número 3.**/


SELECT nombre
FROM PERSONAL_MEDICO1 AS p
INNER JOIN CONSULTA1 AS c ON p.id_medico = c.id_medico
WHERE c.id_paciente = 3;


/**7. Seleccionar Pacientes (nombre e identificador) que no han tenido consulta con ningún enfermero o enfermera.**/
select nombre,id_paciente
from PACIENTES1 
where id_paciente not in (select id_paciente from CONSULTA1 where id_medico in( select id_medico from PERSONAL_MEDICO1 where profesion = 'Enfermera'))


/**8. Seleccionar Pacientes (nombre e identificador) que han tenido consulta con personal medico numero 5 y 3.**/


select p.nombre, p.id_paciente, id_medico
from PACIENTES1 as p
inner join CONSULTA1 as c on p.id_paciente = c.id_paciente
where id_medico in(5,3)

/**9.Pacientes (nombre e identificador) a los que nunca se les ha recetado nada**/

select p.nombre, p.id_paciente 
from PACIENTES1 as p
inner join CONSULTA1 as c on p.id_paciente = c.id_paciente
left join RECETA1 as r on c.id_consulta = r.id_consulta
where r.id_consulta is null
select * from CONSULTA1
select * from RECETA1
/**11.	Pacientes que no han ido a consulta en todo el año 2005.**/
select *
from PACIENTES1 as p
left join CONSULTA1 as c on p.id_paciente = c.id_paciente
where YEAR(c.fecha) <> 2005


/**12.	Pacientes menores de 36 años que asistieron a consulta y no se les receto nada.**/
select p.nombre, p.id_paciente
from PACIENTES1 as p
inner join CONSULTA1 as c on p.id_paciente = c.id_paciente
left join RECETA1 as r on c.id_consulta = r.id_consulta
where edad < 36 and r.id_consulta is null


/**13.Edad promedio de los pacientes atendidos por Médicos Especialistas, en el año 2022**/
select AVG(p.edad) as edad_promedio
from PACIENTES1 as p
inner join CONSULTA1 as c on p.id_paciente = c.id_paciente
inner join PERSONAL_MEDICO1 as m on c.id_medico = m.id_medico
where m.profesion = 'Medico especialista' 
and YEAR(c.fecha) = 2022


/**14.Indicar el nombre del paciente de mayor edad atendido en el año 2022.**/
select TOP 1 p.nombre, MAX(p.edad) as max_edad
from PACIENTES1 as p
inner join CONSULTA1 as c on p.id_paciente = c.id_paciente
where YEAR(c.fecha) = 2022
group  by p.nombre 
order by max_edad desc

select * from CONSULTA1

/**15.Crear una vista de la consulta de pacientes que no hayan sido atendido durante el año 2022 y que sean jubilados
(según norma Argentina para que sea jubilado el hombre deberá ser mayor de 65 años y las mujeres mayores de 60 años)**/

create view vista_1
as
select p.id_paciente,p.nombre,c.fecha
from PACIENTES1 as p
left join CONSULTA1 as c on p.id_paciente = c.id_paciente
where YEAR(c.fecha) not in(2022)
and (p.genero = 'M' and p.edad >=65) or (p.genero = 'F' and p.edad >=60)


/**16.	Indicar los pacientes que tienen de alguna letra F y que hayan sido atendido durante el 2020**/

select p.id_paciente, nombre
from PACIENTES1 as p
inner join CONSULTA1 as c on p.id_paciente = c.id_paciente
where nombre like '%F%'
and YEAR(c.fecha) = 2020




/**17.	Indicar los Médicos especialistas que contengan la letra s y que hayan atendido durante el 2021.**/
create procedure MedicosEspecialistasConSConConsultaEn2021
as
select p.nombre, c.fecha
from PERSONAL_MEDICO1 as p
inner join CONSULTA1 as c on p.id_medico = c.id_medico
where p.nombre like '%S%' and YEAR(c.fecha)=2021
go
exec MedicosEspecialistasConSConConsultaEn2021

/**18.	Por cuestiones de optimización de la base de datos se necesita eliminar las consultas que se han realizado durante la década del 90,
desarrollar un procedimiento almacenado que lo permita.**/

CREATE PROCEDURE EliminarConsultasDecada90
AS
BEGIN
    DELETE FROM CONSULTA1
    WHERE YEAR(fecha) BETWEEN 1990 AND 1999;
END;


/**21.	Indicar aquellas enfermeras que se incorporaron durante el 2020**/
create procedure EnfermerasIncorporacion2020
as
select nombre, fecha_incorporacion
from PERSONAL_MEDICO1
where YEAR(fecha_incorporacion) = 2020
go
exec EnfermerasIncorporacion2020



/**23.Indicar todos los pacientes que no se han atendido este año y que sus datos empiecen con la letra R**/
create procedure PacientesNoAtendidosEn2023Con1eraLetraR
as
select p.nombre
from PACIENTES1 p
left join CONSULTA1 as c on p.id_paciente = c.id_paciente
where p.nombre like 'R%' and YEAR(c.fecha) <> 2023
go
exec PacientesNoAtendidosEn2023Con1eraLetraR


/**24.Indicar todos los pacientes que no se han atendido durante el 2020 o que sus datos contengan la letra s**/
select p.nombre
from PACIENTES1 as p
left join CONSULTA1 as c on p.id_paciente = c.id_paciente
where YEAR(c.fecha) <> 2020 or p.nombre like 'S%'
go


/**25.	Desde una vista mostrar todos los médicos especialistas que se han incorporado en el 2005 y que sus datos tengan al menos una vocal**/
create view vista2
as
select nombre
from PERSONAL_MEDICO1
where profesion = 'Medico Especialista'
and  YEAR(fecha_incorporacion) = 2005
and nombre like '%[aeiouAEIOU]%'
select * from vista2

/**26.	Mostrar la cantidad de consultas que tuvo cada paciente**/
select p.nombre, p.id_paciente, COUNT(*) as cantidadconsultasdecadapaciente
from PACIENTES1 as p
inner join CONSULTA1 as c on p.id_paciente = c.id_paciente
group by p.nombre, p.id_paciente



/**27.	Desde una vista, mostrar la cantidad de consultas que tuvieron cada Médicos (Especialistas y General)**/
create view vista3
as
select p.nombre, p.id_medico, COUNT(*) as cantdeconsultas
from PERSONAL_MEDICO1 as p
inner join CONSULTA1 as c on p.id_medico = c.id_medico
where p.profesion = 'Medico especialista' or p.profesion = 'Medico General'
group by p.nombre, p.id_medico 
