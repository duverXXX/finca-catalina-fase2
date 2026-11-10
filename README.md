# Fase II - Finca Catalina
**Sistema de Gestion de Residuos Organicos Agroindustriales** - Mapeo ORM y operaciones CRUD con Hibernate.
Lenguaje de Programacion 3 - Uniremington (ING-PROY-3).

## Requisitos
- JDK 17 o superior
- Maven 3.8+
- MySQL / MariaDB (XAMPP sirve), en el puerto 3306

## Puesta en marcha
1. Inicia MySQL desde XAMPP.
2. Crea la base de datos: importa `database/gestion_residuos.sql` en phpMyAdmin
   (o usa tu script de la Fase I; Hibernate trabaja con `hbm2ddl.auto=update`).
3. Si tu MySQL tiene clave, edita `src/main/resources/hibernate.cfg.xml` (usuario/clave).
4. Compila y ejecuta:
   ```
   mvn clean compile
   mvn exec:java
   ```
   o ejecuta `com.fincacatalina.gestionresiduos.app.Main` desde IntelliJ / Eclipse / NetBeans.
5. Toma capturas de la consola y de phpMyAdmin para el PDF de entrega.

## Estructura (paquetes logicos)
```
modelo/    Entidades JPA: Usuario, FuenteResiduo, TipoResiduo, IngresoResiduo,
           Tratamiento, LoteTratamiento, ConsultaApi
dao/       Dao<T,ID> (interfaz) y GenericDao<T,ID> (implementacion Hibernate)
servicio/  UsuarioServicio, FuenteResiduoServicio, TipoResiduoServicio, IngresoResiduoServicio
util/      HibernateUtil (SessionFactory)
app/       Main (prueba CRUD)
```

## Que demuestra Main
- CRUD completo sobre **tres** entidades: Usuario, FuenteResiduo y TipoResiduo.
- Un IngresoResiduo que usa las tres relaciones `@ManyToOne`.
- Se puede ejecutar varias veces: usa un correo unico y elimina todo al terminar.

## Subir a GitHub
```
git init
git add .
git commit -m "Fase II: mapeo ORM y CRUD con Hibernate"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
git push -u origin main
```

## Notas
- La clave de `Usuario` se guarda como texto de ejemplo solo para demostrar el mapeo;
  una aplicacion real debe guardar un hash seguro (BCrypt).
- `LoteTratamiento` y `ConsultaApi` quedan mapeadas para las fases siguientes (API externa y web).
