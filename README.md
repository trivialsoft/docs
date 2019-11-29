# Referencia

## Estructura del proyecto

```plain
rloop /
        index.php
        boot.php
        components /
                    core /
                            Api
                            Component
                            ExplicitColumns
                            Factory
                            KeyReader
                            Loop
                            Masso
                            Model
                            TQL
                            TrivialAuthorizer
                            TrivialResponse
                    Grupo
                    Usuario
                    Membresia
                    Permiso
        submodule_1  /
                      components
        submodule_n  /
                      components


```

## Elementos

### Trivial API

### Leer

```plain
 Method: GET
 http://servername:port/loop/@appname/collectionname/level/sort/filter/actions/page/format/pql
```

### Escribir

```plain
Method: POST
http:://servername:port/loop/@appname/anycollectionname
```

### BODY

```json
[
    {
        "modelname":"MODELNAME",
        "MODELNAME":"IDENTIFIER",
        "property_1":"property_value_1",
        "property_2":"property_value_2"
    }
]
```

## Trivial ORM

## Leer una instancia

```php
$instance = orm:instance(MODELNAME, ID, LEVEL);
```

## Leer una lista de instancias

```php
$list = orm::instances(MODELNAME, FILTER, LEVEL, ORDER, SELECT, PAGE);
```

### Parametros

* MODELNAME   Nombre de la clase
* FILTER      Filtro básico array
* LEVEL       Nivel de sub instanciación
* ORDER       Campos de Ordenamiento
* SELECT  **  aun no implementado
* PAGE        Tamano de la pagina a recuperar

### Guardar una instancia

```php
$instance = new classname\classname();
$ins
$instance->save();
```