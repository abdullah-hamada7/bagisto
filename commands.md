1. **Access the Laravel container**

   ```bash
   docker exec -it bagisto_laravel.test_1 bash
   ```

2. **Generate a new app key**
   Inside the container, run:

   ```bash
   php artisan key:generate
   ```

   This command:

   * Generates a random 32-character base64-encoded key.
   * Updates the `.env` file’s `APP_KEY=` line automatically.

   You should see output like:

   ```
   Application key set successfully.
   ```

3. **(Optional) Verify the `.env` file**
   Check that your `.env` contains a line like:

   ```
   APP_KEY=base64:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
   ```

4. **Clear caches (important for Laravel Sail setups)**
   Still inside the container:

   ```bash
   php artisan config:clear
   php artisan cache:clear
   php artisan route:clear
   php artisan view:clear
   ```

5. **Exit the container**

   ```bash
   exit
   ```

6. **Restart the container**

   ```bash
   docker-compose restart laravel.test
   ```