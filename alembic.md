## Alembic

### Initialize Alembic

```bash
alembic init alembic
```

- **Description:** Initialize Alembic

### Generate the first migration script

```bash
alembic revision --autogenerate -m "Initial migration"
```

- **Description:** Generate the first migration script

### Apply the migration

```bash
alembic upgrade head
```

- **Description:** Apply the migration

### This reverts the most recent migration

```bash
alembic downgrade -1
```

- **Description:** This reverts the most recent migration, You can also give revision id

### Check Current Alembic Version

```bash
alembic current
```

- **Description:** Check Current Alembic Version

### Check Alembic history

```bash
alembic history
```

- **Description:** Check Alembic history
