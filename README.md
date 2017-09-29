# IST Environment Emulator

This projects aims to provide easier way of doing assignments and projects that will also work when tested on the official [Técnico Lisbon (IST)] web environment. It attempts to replicate most aspects of the IST web services and to allow the students to not rely on SFTP/SSH/SCP as suggested by some teachers. It also serves as an alternative to installing LAMP/MAMP/WAMP.

As for configuration differences, IST uses Apache as its web server, but this project uses Nginx. Strict CSP rules and PHP settings are enforced in an effort of developing good habits. These can be adapted or removed by modifying `deployment/nginx/nginx.conf` and `deployment/php/php.ini`.

### Installation and Deployment

This project includes config files to create an environment with Nginx, PHP-FPM, [Composer] and MySQL.

* Windows users: only Windows 10 with [Bash on Windows](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide) is supported (required for running the `bin/console` script). You may also need to install `openssl` with `$ sudo apt install openssl`.

* Install [Docker] and [Docker Compose]
* Go to `deployment/`, rename `.env.dist` to `.env` and fill all fields.
* Run `$ bin/console setup`.

* Start environment:

    ```sh
    $ bin/console deploy up -d
    ```

To access the webpage go to [ist-env-emulator.localhost](https://ist-env-emulator.localhost).

* Stop environment:

    ```sh
    $ bin/console deploy down
    ```

* Run commands on the MySQL database:

    ```sh
    $ bin/console mysql
    ```
The prompt will be started with `app/` as the working directory, and you can access any file inside it, e.g., running `SOURCE example.sql` would load the file `app/example.sql`.

* Access logs:

    ```sh
    $ bin/console logs
    ```
Using the flag `-f` activates follow log output. You may also specify the service you want the logs from by appending its name (`mysql`, `php`, `composer` or `nginx`) to the above command, e.g., `$ bin/console logs php`.

### Author

[Miguel de Moura] (me@migueldemoura.com)

### License

See `License.md`

   [Técnico Lisbon (IST)]: <https://tecnico.ulisboa.pt/>
   [Composer]: <https://getcomposer.org/download/>
   [Docker]: <https://docs.docker.com/engine/installation/>
   [Docker Compose]: <https://docs.docker.com/compose/install/>
   [Miguel de Moura]: <https://migueldemoura.com/>
