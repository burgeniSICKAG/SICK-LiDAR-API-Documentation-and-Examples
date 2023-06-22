# How to handle HTTP requests

## How to get started with Insomnia?

> **NOTE**
>
> Insomnia is an open-source software that allows you to create and test your own APIs. The programme is operated by Kong Inc. and the standard version can be downloaded for free. Additional functions can be unlocked through a monthly subscription.
>
> Insomnia offers a very clear user interface whichis easy to use. By simply importing plugins, which have to be created ones, Insomnia can quickly and easily handle challenge & response authentication.

1. Download and install [Insomnia](https://insomnia.rest/download) on you PC.
2. Download the [Insomnia REST Plugin](insomnia-plugin-srt-rest.zip)
4. Extract the .rar file and follow these instructions:
    1. Click on `Application` in the Toolbar
    2. Press `Preferences`
    3. Navigate to `Plugins`
    4. Click on `Reveal Plugins Folder`
    5. Now copy the insomnia-plugin-srt-rest folder in the `plugins` folder of Insomnia
    6. Press `Reload Plugins`

:white_check_mark: If everything worked well, you will see the plugin listed.

</br>
</br>

# How to use Insomnia for HTTP requests

> **NOTE**
> 
> You can import these [Insomnia file]() to have a look on all available GET- and POST- requests or write the requests manually.

---
</br>
</br>


## Option 1: Import Insomnia file

1. Click on `Application` in the Toolbar
2. Press `Preferences`
3. Navigate to `Data`
4. Click on `Import` and choose [this file]()

:white_check_mark: You are now able to use all these requests.

---
</br>
</br>


## Option 2: Write requests manually

</br>
</br>

### Write GET requests manually

1. Open a web browser or Insomnia
2. Type in the following URL:
            
        http://192.168.0.1/api/LocationName


:white_check_mark: When the GET request is executed, the response contains the corresponding values.

>:exclamation: Make sure, that you enter the correct IP address. Variable LocationName shows you the name of the device. For more variables and methods, have a look at the [Telegram Listing](https://sick.com/8014631).

</br>
</br>

### Create Insomnia environment

> **NOTE**
>
> If you want to execute POST requests, you need to log in yourself with an user level. To do this, you must create an enviroment.

1. Navigate to environment and click the `+` Button
2. Rename the environment
3. Enter the following snippet into the environment:

        {
            "address": "192.168.0.1",
            "user": "Service",
            "password": "servicelevel",
            "enableAuthentification": true
        }

:white_check_mark: You are now authenticated as Service. You are able to work with POST requests.

> :exclamation: Make sure, that you enter the correct IP address.

</br>
</br>

### Write POST request manually

1. Press the `+` Button and create a new HTTP request.
2. Choose `POST` instead of `GET`.
3. Type in the following URL:

        http://192.168.0.1/api/LocationName

4. Enter the following snippet into the environment:

        {
	        "data": {
	        	"LocationName": "CustomerDevice01"
	        }
        }

:white_check_mark: You have now changed the DeviceName.

>:exclamation: Make sure, that you enter the correct IP address. Variable LocationName shows you the name of the device. For more variables and methods, have a look at the [Telegram Listing](https://sick.com/8014631).

</br>
</br>

# How to use OpenAPI for HTTP requests

> **NOTE**
> 
> You can use the [OpenAPI documentation](openapi-picoScan.json) for execute HTTP requests.

</br>
</br>

## How to use OpenAPI with SwaggerHub

1. Create an Account for using [SwaggerHub](https://swagger.io/).
2. Download the [OpenAPI documentation](openapi-picoScan.json).
3. Open SwaggerHub and Navigate to `+ Create New`.
4. Click on `Import and Document API`.
5. Search for the OpenAPI documentation in your download folder and press `IMPORT`.

:white_check_mark: You are now able to use the OpenAPI documentation for HTTP requests.

</br>
</br>

## How to use OpenAPI documentation on GitLab

1. Navigate to [OpenAPI documentation](openapi-picoScan.json).
2. GitLab should now show the rendered OpenAPI file. GitHub unfortunately does not support this feature.

:white_check_mark: You are now able to work with the OpenAPI documentation.