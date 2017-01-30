generic-SDK library
==========

**A Javascript library to perform API request in javascript using JSONP.**

## Documentation
- Developer Docs: [https://github.com/setni/generic-SDK/wiki](https://github.com/setni/generic-SDK/wiki)

## Current Release
- <b>0.1.6</b> : Set timeout parameter.

## Changes
- <b>0.1.3</b> : Add default apikey parameter.
- <b>0.1.0</b> : Test for 3 differents API.

## Requirement for using
**No requirement**


##Example of use

###Declaration

```javascript
//declare sdk
    (function(d, s, id){
        var js, fjs = d.getElementsByTagName(s)[0];
        if (d.getElementById(id)) {return;}
        js = d.createElement(s); js.id = id;
        js.src = "sdk.js";
        fjs.parentNode.insertBefore(js, fjs);

        // listerner
        if (js.readyState){  //Internet Explorer
            js.onreadystatechange = function()
            {
                if (js.readyState == "loaded" ||
                    js.readyState == "complete"){
                        js.onreadystatechange = null;
                        //call a personnal function after loading
                        test.opendata();
                }
            }
        } else { //Others
            js.onload = function ()
            {
                 //call a personnal function after loading
                test.opendata();
            };
        }
    }(document, 'script', 'generiquesdk'));

```

###Simple use and query

```javascript
var test = {
        opendata: function () {
            GeneriqueSDK = new GeneriqueSDK();
            GeneriqueSDK.setApikey(API_KEY);
            GeneriqueSDK.setUrl("https://psa.opendatasoft.com/api/records/1.0/search/");
            GeneriqueSDK.setTimeOut(5);

        },

        request: function () {
            var e = document.getElementById("dataset");
            var dataset = e.options[e.selectedIndex].text;
            var query = document.getElementById("query").value || "FAURECIA SIEGE";
            var data = {
                dataset: dataset,
                lang: "fr",
                q: query,
                rows: 100
            };

            GeneriqueSDK.get(data, function (r) {
                document.getElementById("nhits").innerHTML = JSON.stringify("nb result: "+r.nhits);
                document.getElementById("main").innerHTML = JSON.stringify(r.records);
                console.log(r);
            });
        }
    };
```


## Bugs
If you find a bug, please post it as a new issue on the GitHub repository with <a https://github.com/setni/Angular.js-project/issues">this information in your report</a>.

## Contribute
If you would like to contribute to the project, have at it.  <a href="https://help.github.com/articles/fork-a-repo">Fork the Tweetledee project</a>, include your changes, and <a href="https://help.github.com/articles/using-pull-requests">submit a pull request</a> back to the main repository.

## License
MIT License - see the LICENSE.txt file in the source distribution

✪ Thomas
