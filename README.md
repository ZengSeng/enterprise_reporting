# Enterprise Reporting (dbt project)

This repository contains a dbt project for enterprise reporting.

## Getting Started

### 1. Install dbt

It’s recommended to use a virtual environment.

```bash
# Navigate to your workspace
cd C:\repo\dbt_workspace

# Create a virtual environment
python -m venv .venv

# Activate the virtual environment
.\.venv\Scripts\activate

# Install dbt (example: dbt-core with SQL Server adapter)
pip install dbt-core dbt-sqlserver
```

Replace `dbt-sqlserver` with the adapter for your database (e.g., `dbt-postgres`, `dbt-bigquery`, `dbt-snowflake`, etc.).

---

### 2. Configure dbt Profiles

dbt looks for a `profiles.yml` file in the `.dbt` folder inside your user directory:

- **Windows:** `C:\Users\<YourUsername>\.dbt\profiles.yml`  
- **Linux/Mac:** `~/.dbt/profiles.yml`

Example `profiles.yml`:

```yaml
enterprise_reporting:
  target: dev
  outputs:
    dev:
      type: sqlserver
      threads: 4
      host: localhost
      user: my_user
      password: my_password
      database: my_database
      schema: my_schema
      port: 1433
```

Update the values according to your database connection.

---

### 3. Create and Initialize a dbt Project

If you don’t already have a dbt project:

```bash
# Inside your workspace folder
dbt init enterprise_reporting
```

This will create the standard dbt folder structure.  
Since this repo already includes a dbt project, you can just clone it and start working.

---

### 4. Run dbt

Once everything is set up:

```bash
# Activate your virtual environment
.\.venv\Scripts\activate

# Navigate to your project folder
cd enterprise_reporting

# Test connection
dbt debug

# Run models
dbt run

# Run tests
dbt test
```

---

## Folder Structure

```
enterprise_reporting/
│
├── analyses/
├── macros/
├── seeds/
├── snapshots/
├── tests/
├── dbt_project.yml
├── README.md
```
