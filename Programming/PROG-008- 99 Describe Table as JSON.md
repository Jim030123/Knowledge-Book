```sql
SELECT json_agg(
    json_build_object(
        'field', column_name,
        'type', data_type,
        'null', is_nullable,
        'default', column_default,
        'max_length', character_maximum_length,
        'numeric_precision', numeric_precision,
        'numeric_scale', numeric_scale
    )
) AS columns
FROM information_schema.columns
WHERE table_schema = 'public'
  AND table_name = 'your_table';

```