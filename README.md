SmartCool : Monitoring the refrigerator inventory and temperature using Internet of Things and a mobile application

The SmartCool system is designed to enhance the management of refrigerator contents by integrating IoT technology for real-time monitoring of temperature and inventory levels. This system aims to reduce food waste, improve user convenience, and streamline grocery management through an intuitive mobile application that provides instant alerts and detailed insights.

User Requirements:
1.Stable network connection
2.Smartphone with the SmartCool mobile application

Developer Requirements:
1.Laptop/Desktop
2.Visual Studio Code for application development
3.Node.js for backend development
4.MongoDB for database management
5.React Native for mobile application development


Hardware Components:
1.Raspberry Pi 3 Model B Board
2.Load Cell
3.HX711 Weighing module
5.DHT22 Humidity and Temperature module
6.Breadboard and jumper wires
7.10K Ohm Resistors

Additional Components:
1.5V Power Supply Adapter
2.USB to mini-USB cable
3.HDMI cable






-------------------------------------------- INSTALLATION --------------------------------------------------------------


------------Set up Raspberry Pi------------------


1. Download the Raspberry Pi imager to your computer.
2. Then select Raspberry Pi OS - 32-bit or higher version and boot it to the 16GB or higher storage Micro SD card.
3. Set up the Raspberry Pi with the booted Micro SD card.
4. Connect the sensors according to the wiring diagram in the attached files



------------Set up Running Environment-------------

Step 1: Unzip the Folders
Unzip the React Native (mobile_app) and Node.js backend (mobile_app_backend) folders.
Open the unzipped folders in Visual Studio Code.


Step 2: Install Node Modules
1. For both mobile_app and mobile_app_backend folders:
	- Open the terminal in Visual Studio Code.
	- Run npm i following command in the termianl to install the required Node modules


Step 3: Set Up the Django Application on Raspberry Pi
1. Open the terminal on your Raspberry Pi.
2. Create a new folder for the Django application.
3. Create a virtual environment:
	- python -m venv myenv
	- source myenv/bin/activate
4. Install required libraries:
	- pip install Adafruit-DHT==1.4.0 asgiref==3.8.1 distlib==0.3.8 Django==5.1 djangorestframework==3.15.2 filelock==3.15.4 HX711==0.1.4 pip==23.0.1 platformdirs==2.2.0 RPi.GPIO==0.7.1 	  setuptools==66.1.1 sqlparse==0.4.5 virtualenv==20.26.3
5. Create a new Django project and app:
	- django-admin startproject smartcool
	- cd smartcool
	- python manage.py startapp sensors


Step 4: Copy Code to Django Application
1. Navigate to the django_app folder in the provided zipped files:
	- Open the app_level folder, and copy the code from views.py.
	- Paste the copied code into the views.py file located in the sensors app of your newly created Django application.
2. Update URLs:
	- Copy the code from urls.py in the app_level folder of the django_app.
	- Paste it into the urls.py file within the sensors app.
3. Configure Project Settings:
	- Open the project_level folder in django_app and copy the settings from the settings.py file.
	- Paste this into your Django project's settings.py file, located in the smartcool folder.
	- Add 'sensors' to the INSTALLED_APPS section in settings.py.
4. Update Project URLs:
 	- Copy the urls.py file content from the project_level folder.
	- Paste it into the urls.py file in the smartcool folder of your Django project.
5. Calibrate the Load Cells:
	-Follow the prompts in the terminal to add a known weight to each load cell and press Enter. Make sure you change value1 and value2 in views.py according to your known weights for 	 proper calibration


Step 5: Run the Django Application 
	- source myenv/bin/activate
	- python manage.py runserver 0.0.0.0:8080


Step 6: Set Up MongoDB
1. Create a new cluster in MongoDB.
2. Update the DB_URL in the .env file within the mobile_app_backend folder with your new cluster URL.


Step 7: Run the Node.js Backend
1. Open the mobile_app_backend folder in Visual Studio Code.
2. Start the backend server by running npm start on the terminal


Step 8: Run the Mobile Application
1. Navigate to the mobile_app folder and start the app by running npm start in the terminal
2. Run the app on an Android emulator or use Expo Go on your mobile device:
	- For Android Emulator: Use Android Studio to run an emulator, such as Google Pixel 8.
	- In the terminal, select the option to run the app on the emulator or scan the QR code with Expo Go on your phone.


Additional Notes
1. Known Weights: Ensure that the weights used for calibration are known values. Update value1 and value2 in views.py for accurate load cell calibration.
2. Adjust Quantity Calculations: Modify the line in views.py where quantities are calculated to use your specific weight values:
	- quantity1 = weight1 / <your_known_weight>
3. MongoDB Setup: Make sure to create a new cluster in MongoDB and update the DB_URL in the .env file within the mobile_app_backend folder with the new cluster URL to ensure proper database connectivity.
4. Issue with Unzipped Folders: If the unzipped folders do not work as expected, you can clone the latest version of the SmartCool project from the GitHub repository
	- git clone https://github.com/m-asjedh/SmatCool-Mobile-App.git
	- git clone https://github.com/m-asjedh/SmartCool_Nodejs_backend.git



