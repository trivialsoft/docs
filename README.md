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
http://servername:port/loop/@appname/anycollectionname
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
use \core\Factory\Factory as orm;
...
$instance = orm::instance(MODELNAME, ID, LEVEL);
```

## Leer una lista de instancias

```php
use \core\Factory\Factory as orm;
...
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

## Estructura de un componente

> Se ejemplifica con el siguiente ejemplo:

```plain

Usuario(carpeta)/Usuario.php             -- Modelo
                /UsuarioComponent.php    -- Script Backend
```

## Modelo Persistente

> Un modelo Persistente, es la clase que se usa para representar objetos persistidos en la base de datos, tienen la estructura que se ejemplifica a continuación:

```php
<?php
/**
*  file location: components/Usuario/Usuario.php 
*/
namespace Usuario;
use \core\Model\Model as Model;
class Usuario extends Model implements \JsonSerializable {
	public $Usuario;
	public $Nombre;
	function __construct()
	{
		parent::__construct();
	}

function subinstances()
	{
		return array("Ciudad"=>"Ciudad");
	}

public function jsonSerialize() 
	{
	return [
		'Usuario' => $this->Usuario,
		'Nombre' => $this->Nombre
		];
		}
	}
?>
```

## Modelo No Persistentes

> Un modelo No Persistente es una clase que se usan para poblar información de componente y que no guarda relacion directa con una entidad , tienen
la estructura que se ejemplifica a continuación:

```php
<?php
/**
*  file location: components/Home/Home.php
*/
namespace Home;
class Home {
function __construct()
	{
	}

function Nombre()
	{
		return "TrivialSoft";
	}
function select()
	{
		return array(0=>$this);
	}
}
?>
```