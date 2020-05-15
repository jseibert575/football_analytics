# football_analytics

Data can be loaded from two places, either https://github.com/guga31bb/nflfastR-data or https://github.com/ryurko/nflscrapR-data.

Important note: Some of the data is wrong! The only example I've found of this so far is that it credits Jarvis Landry with a touchdown in week 1 of the 2019 season, but he didn't score one. To fix that, once you've loaded the data and stored it in some pandas dataframe df, just run:

```
wrong_td_ind = (data.query("receiver_player_name == 'J.Landry'")
                    .query("touchdown == 1")
                    .query("season == 2019")
                    .query("week == 1")
                    .index.tolist()
               )

if wrong_td_ind:
    data.at[wrong_td_ind[0],'touchdown'] = 0
```
If you find any other issues, they can be fixed in a similar way.
