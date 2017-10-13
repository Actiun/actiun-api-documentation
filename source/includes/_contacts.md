# Contactos

Los contactos representan los clientes y proveedores los cuales se encuentran asociados a tu cuenta.

## Objeto Contacto

Un contacto contiene los siguientes atributos:

Atributo | Tipo | Descripción
--------- | ------- | -----------
`id` | integer | Identificador único que representa un contacto.
`name` | string | Nombre del contacto.
`identification` | string | Número de identificación utilizado para la facturación. Ej. RFC, cédula, etc.
`billing_address_email` | string | El correo o correos electrónicos a donde se envian las facturas. En caso de tener varios correos deben ir separados por una coma.
`alias` | string | Sobrenombre que se le desee agregar para futuras referencias de busquedar por nombre.
`bill_with_parent` | boolean | Si el contacto tiene una cuenta padre, se desea facturar con la información fiscal y dirección de dicho contacto.
`bill_with_shipping`| string | En caso de que el contacto tenga una dirección fisica y se desee utilizar la misma direccón para su facturación.
`billing_address` | object | La dirección fiscal del contacto.
`shipping_address` | object | La dirección física del contacto.

## Consultar un Contacto

```shell
# Ejemplo de llamada
curl "https://api.actiun.com/contacts/1" \
  -H "Authorization: {LLAVE_PRIVADA}" \
  -H "Content-Type: application/json"
```

> Resultado

```json
{
  "contact": {
    "id": 2145,
    "name": "ACME SA DE CV",
    "identification": "ACM131115G35",
    "billing_address_email": "compras@spt.com.mx",
    "alias": "",
    "bill_with_parent": false,
    "bill_with_shipping": false,
    "parent": null,
    "billing_address": {
      "street": "MANUEL  ALVAREZ  BRAVO",
      "street_2": null,
      "outdoor_number": "902",
      "interior_number": "",
      "neighborhood": "PASEO  REAL",
      "city": "GENERAL ESCOBEDO",
      "state": "NLE",
      "country": "MX",
      "zipcode": "66072",
      "full": "MANUEL  ALVAREZ  BRAVO, 902, PASEO  REAL, C.P. 66072 GENERAL ESCOBEDO, Nuevo León, México"
    },
    "shipping_address": {
      "street": "AV CUCHARAS",
      "street_2": null,
      "outdoor_number": "100",
      "interior_number": "",
      "neighborhood": "PARQUE  IND  ESCOBEDO",
      "city": "GENERAL ESCOBEDO",
      "state": "NLE",
      "country": "MX",
      "zipcode": "66072",
      "full": "AV CUCHARAS, 100, PARQUE  IND  ESCOBEDO, C.P. 66072 GENERAL ESCOBEDO, Nuevo León, México"
    }
  }
}
```

Endpoint que permite consultar un contacto registrado en la aplicación.

### HTTP Request

`GET https://api.actiun.com/contacts/:id`

### URL Parameters

Parámetro | Descripción
--------- | -----------
id | El identificador del contacto que deseas obtener la información.


## Lista de Contactos

```shell
# Ejemplo de llamada
curl "https://api.actiun.com/contacts" \
  -H "Authorization: {LLAVE_PRIVADA}" \
  -H "Content-Type: application/json"
```

> Resultado

```json
contacts: [
  {
    "id": 1,
    "name": "ACME SA DE CV",
    "identification": "ACM120412I11",
    "alias" : ""
  },
  {
    "id": 2,
    "name": "ACME SA DE CV",
    "identification": "ACM120412I11",
    "alias" : ""
  }
]
```

Endpoint que permite consultar un listado de los contactos registrados.

### HTTP Request

`GET https://api.actiun.com/contacts`

### Query Parameters

Parámetro | Tipo | Descripción
--------- | ------- | -----------
query | string | Cadena de texto que se quiere utilizar para buscar los contactos que en el nombre contienen dicho texto

## Crear Contacto

```shell
# Ejemplo de llamada básica
curl "https://api.actiun.com/contacts" \
  -X POST \
  -H "Authorization: {LLAVE_PRIVADA}" \
  -H "Content-Type: application/json" \
  -d '{
   "name": "Empresa Patito SA de CV",
   "identification": "ACM131115G35"
 }'
```

> Resultado

```json
{
  "contact": {
    "id": 50,
    "name": "Empresa Patito SA de CV",
    "identification": "ACM131115G35",
    "billing_address_email": null,
    "alias": null,
    "bill_with_parent": false,
    "bill_with_shipping": true,
    "depth": 0,
    "credit_days": 0,
    "payment_method_id": null,
    "payment_type_id": null,
    "account_number": null,
    "parent": null,
    "billing_address": null,
    "shipping_address": null
  }
}
```

Endpoint que permite crear un nuevo contacto.

### HTTP Request

`POST https://api.actiun.com/contacts`

## Editar Contacto

```shell
curl https://api.actiun.com/contacts/50 \
    -X PUT \
    -H "Authorization: {LLAVE_PRIVADA}" \
    -H "Content-Type: application/json" \
    -d '{
  "alias": "Cuack cuack",
  "billing_address_email": "macpato@millonario.com"
}'
```

> Resultado

```json
{
  "contact": {
    "id": 50,
    "name": "Empresa Patito SA de CV",
    "identification": "ACM131115G35",
    "billing_address_email": "macpato@millonario.com",
    "alias": "Cuack cuack",
    "bill_with_parent": false,
    "bill_with_shipping": true,
    "depth": 0,
    "credit_days": 0,
    "payment_method_id": null,
    "payment_type_id": null,
    "account_number": null,
    "parent": null,
    "billing_address": null,
    "shipping_address": null
  }
}
```
Endpoint que permite editar un contacto existente.

### HTTP Request

`PUT https://api.actiun.com/contacts/:id`

### URL Parameters

Parámetro | Descripción
--------- | -----------
id | El identificador del contacto que deseas actualizar



## Eliminar Contacto

```shell
curl "https://api.actiun.com/contacts/50" \
  -X DELETE
  -H "Authorization: {LLAVE_PRIVADA}"
```

Endpoint que te permite borrar un contacto. Si el cliente cuenta con información relacionada como facturas de ventas, facturas de gastos u otro documento, este no será eliminado en su totalidad solo será marcado como eliminado (soft delete) y no aparecerá en las busquedás principales.

### HTTP Request

`DELETE https://api.actiun.com/contacts/:id`

### URL Parameters

Parámetro | Descripción
--------- | -----------
id | El identificador del contacto que deseas eliminar