# PostgreSQL Docker Compose

This is a Docker Compose configuration file that sets up a PostgreSQL database using Docker. It allows you to easily create and manage a PostgreSQL container with the specified configuration.

## Prerequisites

- Docker: Ensure that Docker is installed on your system before using this Docker Compose configuration.

## Usage

1. Clone the repository:

   ```bash
   git clone https://github.com/mehedi-sust/postgres-docker-compose.git
   ```

2. Navigate to the project directory:
   ```bash
   cd postgres-docker-compose
   ```

3. Update the `docker-compose.yml` file:

   - Adjust the environment variables in the `environment` section as per your requirements. The available variables are:
   - `POSTGRES_USER`: PostgreSQL username (default: `mehedi`)
   - `POSTGRES_PASSWORD`: PostgreSQL password (default: `12345Me`)
   - `POSTGRES_DB`: PostgreSQL database name (default: NULL)

**Note:** If you want to create a custom database, you can do so by defining the `POSTGRES_DB` environment variable in the docker-compose.yml file. By default, the database name is not specified in the YAML file. However, you can follow step 6 in the instructions to connect to the PostgreSQL container and using the `psql` command  create your desired database. Also if you want to use a specific version of postgres just update this line `image: postgres:latest` and replace `latest` with your desired version number.

4. Start the PostgreSQL container:

   ```bash
   docker-compose -f docker-compose.yml up -d
   ```

   This command will start the PostgreSQL container in detached mode, running in the background.

5. Verify the container is running:

   ```bash
   docker-compose -f docker-compose.yml ps
   ```
   You should see the PostgreSQL container listed with the status "Up".

6. Connect to the PostgreSQL database:

   - You can connect to the PostgreSQL database using various tools, such as:
   ```bash
   sudo docker exec -it <container_name> psql -U <username>
   ```

   Replace <container_name> with the name of the PostgreSQL container (e.g., postgres_db_1) and <username> with the PostgreSQL username (default: mehedi).

   - GUI tools:
You can use database management tools like pgAdmin, DBeaver, or any other PostgreSQL client to connect to the database. Use the following connection details:

      - Host: localhost
      - Port: 5432
      - Username: `<username>`
      - Password: `<password>`
      - Database: `<database>`




7. Stop the PostgreSQL container:

```bash
Copy code
docker-compose -f docker-compose.yml down   
```

## License

This project is licensed under the MIT License. 

See the [LICENSE](LICENSE) file for more information.



**Note:** The usage instructions assume that the Docker Compose file is named `docker-compose.yml` and it's located in the root directory of your project. Adjust the command accordingly if your file name or location is different. Feel free to fork this repository and customize the configuration according to your specific needs.

Make sure to replace `<username>`, `<password>`, and `<database>` with the appropriate values for your PostgreSQL setup.
