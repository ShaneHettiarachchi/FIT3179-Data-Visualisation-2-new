# FIT3179-Data-Visualisation-2

Data Visualisation comparing large scale natural disaster events in Australia and the World.

Australia Shapefile: https://www.kaggle.com/datasets/christopherrickard/aust-shape?resource=download 

World Natural Disaster Dataset source: https://www.kaggle.com/datasets/elvinrustam/global-disaster-events-20002025/data

Australia fires 2019 dataset: https://www.kaggle.com/datasets/gabrielbgutierrez/satellite-data-on-australia-fires
- Dataset processed to only have 2019 entries

Australia fires state by state dataset: https://www.data.gov.au/data/dataset/fires-in-australia-s-forests-2016-21-2024

World fires dataset source: https://www.kaggle.com/datasets/willianoliveiragibin/wildfires
The datasets from this were filtered to only have Australian data.





AI declarations:
Here I will go through the places I used AI to help me with this assignment.

Index.html -

dropdown disaster selector:
     I used GitHub Copilot, to help create the functionality for the dropdown disaster selctor
      the generated code is 28 lines of code, slightly altered to fit the context of my project
      only 1 iteration was used.


Year selector dropdown box:
        I used chatGPT to generate the 13 lines of code to adjust the colours of the drop down box below the bar chart. 
        Code has been tweaked to fit the context of this project


2019Fires.json - 
        I used microsoft copilot to help me create the longitude and latitude mapping to the Australian map functionality.
        The code has been tweaked to fit this context.
        The code is here:
            "transform": [
                { "calculate": "round(datum.longitude * 2) / 2", "as": "lon_rounded" },
                { "calculate": "round(datum.latitude * 2) / 2", "as": "lat_rounded" },
                {
                "aggregate": [
                    { "op": "count", "as": "fire_count" }
                ],
                "groupby": ["lon_rounded", "lat_rounded"]
                }


2019Heatmap.json - 
        I used Microsoft copilot to help me extract the count of fires and map them to the months of the year for the heatmap.
        The code is here:
            "transform": [
                {
                "calculate": "toDate(datum.acq_date)",
                "as": "date"
                },
                {
                "timeUnit": "month",
                "field": "date",
                "as": "month"
                },
                {
                "aggregate": [{"op": "count", "as": "fire_count"}],
                "groupby": ["month"]
                }