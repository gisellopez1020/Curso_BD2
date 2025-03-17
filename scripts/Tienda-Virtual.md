# Script de Modelado de Tienda Virtual

**_Colección Clientes_**

```
db.createCollection("Clientes", {
    "capped": false,
    "validator": {
        "$jsonSchema": {
            "bsonType": "object",
            "title": "Clientes",
            "properties": {
                "_id": {
                    "bsonType": "objectId"
                },
                "nombre": {
                    "bsonType": "string"
                },
                "direccion": {
                    "bsonType": "object",
                    "properties": {
                        "ciudad": {
                            "bsonType": "string"
                        },
                        "codigoPostal": {
                            "bsonType": "number"
                        },
                        "ubicacion": {
                            "bsonType": "string"
                        }
                    },
                    "additionalProperties": false
                },
                "telefonos": {
                    "bsonType": "array",
                    "additionalItems": true,
                    "items": {
                        "bsonType": "string"
                    }
                }
            },
            "additionalProperties": false,
            "required": [
                "_id",
                "nombre",
                "direccion",
                "telefonos"
            ]
        }
    },
    "validationLevel": "off",
    "validationAction": "warn"
});
```

**_Colección Pedidos_**

```
db.createCollection("Pedidos", {
    "capped": false,
    "validator": {
        "$jsonSchema": {
            "bsonType": "object",
            "title": "Pedidos",
            "properties": {
                "_id": {
                    "bsonType": "objectId"
                },
                "fechaPedido": {
                    "bsonType": "date"
                },
                "clienteId": {
                    "bsonType": "objectId"
                },
                "detallePedido": {
                    "bsonType": "array",
                    "additionalItems": true,
                    "items": {
                        "bsonType": "object",
                        "properties": {
                            "productoId": {
                                "bsonType": "objectId"
                            },
                            "cantidad": {
                                "bsonType": "number"
                            },
                            "precio": {
                                "bsonType": "double"
                            }
                        },
                        "additionalProperties": false
                    }
                }
            },
            "additionalProperties": false,
            "required": [
                "_id",
                "fechaPedido",
                "detallePedido"
            ]
        }
    },
    "validationLevel": "off",
    "validationAction": "warn"
});
```

**_Colección Productos_**

```
db.createCollection("Productos", {
    "capped": false,
    "validator": {
        "$jsonSchema": {
            "bsonType": "object",
            "title": "Productos",
            "properties": {
                "_id": {
                    "bsonType": "objectId"
                },
                "nombre": {
                    "bsonType": "string"
                },
                "cantidad": {
                    "bsonType": "number"
                },
                "precio": {
                    "bsonType": "double"
                }
            },
            "additionalProperties": false,
            "required": [
                "_id",
                "nombre",
                "cantidad",
                "precio"
            ]
        }
    },
    "validationLevel": "off",
    "validationAction": "warn"
});
```
