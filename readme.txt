Churchill's BetterWeather System v1.0

Description
-----------
I've noticed that most weather scripts seem to be a bit basic in that they just
randomly change the weather at a fixed time. Sometimes they go one step further
and change it at a random time.  What this script does is attempt to mimic 
weather patterns by setting today's weather but also pre-defining potential
weather for 2 days ahead, for both the day and night weather. 

When the weather updates each day it's based on these pre-defined "predictions"  
As with real weather, it's not 100% accurate - sometimes the weather prediction
can be wrong for the days ahead when we actually get to tomorrow or the next
day :)

It is also a little random in that it won't change at a set time every day/night

Day time changes come into effect between 7am and midday.  Night time weather
comes into effect after 8pm, but before midnight.


Editing the optional.xml file
-------------------------
The BetterWeather system as provided will display a reasonably nice report for 
the next few days when you hit F5.

If you wish to change the key mapping because it conflicts with another 
resource, you can do so by editing the appropriate settings in the
optional.xml file.  You may even want to disable the report altogether, if 
you have another resource to handle the UI for the weather reports -  
e.g. to make your existing server branded UI show weather reports, as an 
example, or if you want to use weather reports in your server to 
influence player actions in other resources.  To do this, just modify the 
WeatherReportsEnabled setting to false.

Or you can delete the appropriate lines in the meta file and delete the
optional files altogether if you want it to be even cleaner :)


Export Functions For interacting with other resources
-----------------------------------------------------

in all cases:

WeatherOverNight is nil unless it's between midnight and 7am.
WeatherOverNight and WeatherToday are both nil if it's between 8pm and midnight.


<export function="GetTodaysWeatherDescriptions" http="true" />
	returns WeatherOverNight, WeatherToday, WeatherTonight 
	
	string descriptions to use if you want to display it when
	the user logs onto the server, for example.
	

<export function="GetTodaysWeatherIDs" http="true" />
	returns WeatherOverNight, WeatherToday, WeatherTonight
	
	as before, but the values are the numeric IDs for the weather, 
	rather than strings, just in case you want the raw ids for use
	in your resource.


<export function="GetAllWeatherDescriptions" http="true" />
	returns WeatherOverNight, WeatherToday, WeatherTonight, WeatherTomorrowDay, WeatherTomorrowNight, WeatherDayAfter, WeatherDayAfterNight
	
	longer report for today and the days ahead.

<export function="GetAllWeatherIDs" http="true" />
	returns WeatherOverNight, WeatherToday, WeatherTonight, WeatherTomorrowDay, WeatherTomorrowNight, WeatherDayAfter, WeatherDayAfterNight

	as above but returns numeric ids instead.
	
<export function="GetDayWeatherDescription" http="true" />
	given a weather id, it'll return a string weather description suitable for daytime weather.

<export function="GetNightWeatherDescription" http="true" />
	given a weather id it'll return a string weather description suitable for nighttime weather.


Known issues
------------
* Deliberately ignored sandstorms - they're not relevant outside of the deserts
	and you can't restrict weather to a particular region yet, so it is
	safer to just ignore it completely for now. 
* I don't mind if you find any further issues, it'll help to improve this script!


Future improvements
-------------------
* Maybe tweak the randomness to reduce the random weather events a little.
* Add a html interface to view the weather reports on a server running this resource.
* Please suggest some :)


