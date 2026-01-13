# solid-robot

Cotizador básico en Oracle con tablas, tipos y paquete PL/SQL.

## Uso rápido

1. Ejecuta el esquema:

```sql
@sql/cotizador_schema.sql
```

2. Inserta datos de ejemplo:

```sql
@sql/seed.sql
```

3. Genera una cotización con el paquete:

```sql
DECLARE
  v_items t_items_cotizacion := t_items_cotizacion(
    t_item_cotizacion(1, 2),
    t_item_cotizacion(2, 1)
  );
  v_cotizacion_id NUMBER;
BEGIN
  cotizador_pkg.crear_cotizacion(
    p_cliente_id => 1,
    p_usuario => 'vendedor@empresa.com',
    p_items => v_items,
    p_tasa_impuesto => 0.16,
    p_cotizacion_id => v_cotizacion_id
  );
  DBMS_OUTPUT.PUT_LINE('Cotización creada: ' || v_cotizacion_id);
END;
/
```
