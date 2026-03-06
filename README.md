# NightBar-ISII
Software de gestión de pedidos para disco-bares, tiendas de ventas de bebidas alcohólicas 

# *DIAGRAMA ENTIDAD-RELACIÓN*

erDiagram
    PROVEEDOR ||--o{ PRODUCTO : "surte"
    CLIENTE ||--o{ PEDIDO : "realiza"
    USUARIO ||--o{ PEDIDO : "gestiona"
    PEDIDO ||--|{ DETALLE_PEDIDO : "contiene"
    PRODUCTO ||--o{ DETALLE_PEDIDO : "se incluye en"

    PROVEEDOR {
        int id_proveedor PK
        string nombre_empresa
        string nombre_contacto
        string telefono
        string email
        boolean estado
    }
    
    PRODUCTO {
        int id_producto PK
        int id_proveedor FK
        string nombre
        string tipo
        numeric precio
        boolean estado
    }

    USUARIO {
        int id_usuario PK
        string nombre
        string email
        string password
        string rol
        boolean estado
    }

    CLIENTE {
        int id_cliente PK
        string nombre
        string telefono
        timestamp fecha_registro
    }

    PEDIDO {
        int id_pedido PK
        int id_cliente FK
        int id_usuario FK
        timestamp fecha
        string estado
        numeric total
    }

    DETALLE_PEDIDO {
        int id_detalle PK
        int id_pedido FK
        int id_producto FK
        int cantidad
        numeric precio_unitario
        numeric subtotal
    }