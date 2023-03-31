# Bird Migration Project
### <ins><b>Overview:</b></ins> <br>
In this project my group analyzed bird migration dataset. The dataset contains information about the migration paths of three different birds. 
We used various libraries, visualizations and statistical functions to explore the differences between the migration patterns of these birds and 
identify their distinct characteristics. 

### <ins><b>Goal:</b></ins> <br>
Our goal was to explore each bird's behavior and see whether the migration path of each bird varied. 

### <ins><b>Dataset:</b></ins> <br>
You can access the dataset under all the files in this repository. The name of the file is bird_tracking.csv

```bash
# Importing the dataset
birds = pd.read_csv("bird_tracking.csv")
```

### <ins><b>Libraries:</b></ins><br>
These are the libraries that we imported into the project so that we would be able to complete this project. 
* We used geopy libary to find the country that the bird is in based on its latitude and longitude
* Haversine library is used to calculate the distance between two locations
* Plotly is an important library that allowed us to create visual plots
* We used ipywidgets to create interactive visual

```bash
!pip install geopy --user
!pip install haversine --user

import pandas as pd
import matplotlib.pyplot as plt
from plotly import tools
import plotly as plt
import plotly.express as px
import chart_studio.plotly
from plotly.offline import init_notebook_mode, iplot
init_notebook_mode(connected=True)
import plotly.graph_objs as go
import plotly.figure_factory as ff
from IPython.display import HTML, Image
import plotly.express as px
px.set_mapbox_access_token(open(".mapbox_token").read())
from geopy.geocoders import Nominatim
import ipywidgets as widgets
from ipywidgets import interact, interact_manual
import haversine as hs
```
### <ins><b>Mapbox Visual:</b></ins><br>
In order to be able to display a map with all the geolocations you need to have a mapbox access token. 
You can use the mapbox token provided in this repository under the file named mapbox_token or create your own mapbox token. 

To create a new mapbox_token: <br>
Step 1: Go to https://www.mapbox.com/. <br>
Step 2: Create a new account.<br>
Step 3: Create new access token. <br>

To get the token to the notebook:<br>

```bash
px.set_mapbox_access_token(open(".mapbox_token").read())
```

### <ins><b>Locations:</b></ins><br>
To find the country based on the latitude and longitude, use geopy library and the functions that it has. 

First, you need a latitude and a longitude values. The next step is to use the built in functions of the geopy library
that allows the users to find a location, address and the country based on the geolocation. 

<ins>Example from the project:</ins><br>

```bash
Eric_lat_start = str(Eric['latitude'].iloc[0])
Eric_lon_start = str(Eric['longitude'].iloc[0])

geolocator = Nominatim(user_agent = 'geoapiExercises')
location = geolocator.reverse(Eric_lat_start+","+Eric_lon_start)
address = location.raw['address']
country = address.get('country', '')
country
```

### <ins><b>Distance Calculation:</b></ins><br>
Haversine is a very useful library that allows the users to calculate the distance between two geolocations.

Haversine function = hs.haversine(loc1, loc2)<br>
<ins>Loc1 consists of two values:</ins>
* Latitude
* Longitude

<ins>Example from the project</ins>
```bash
loc1 = (float(Eric_lat_start), float(Eric_lon_start))
loc2 = (first_loc['latitude'].iloc[0], first_loc['longitude'].iloc[0])
to_dist = hs.haversine(loc1,loc2)
```

