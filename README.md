cytoscape-web-service
================================================================================

Web-service on cytoscape.js to layout graphs

Server and it's demo client-side are at:
https://cytoscape-layout-service.herokuapp.com/

## Supported formats
This web-server supports 3 input formats for graphs:
1. SBGN-ML
2. GraphML
3. JSON

## Instructions on how to send a request
Request to layout the graph:
```
POST /layout/:file_format
```
needs to be send to https://cytoscape-layout-service.herokuapp.com, and the type of the request must be 'text' or 'text/plain'.
By default nodes with their positions(x,y) and their dimension(width, height) if given will be returned. If you want edges to be returned as well you should add edges option to the request with it's truth value, which is false by default:
```
POST /layout/:file_format?edges=true
```

The format of the request depends on a format of the graph nodes and edges:
### JSON:

An array where the first element of the array is also an array that consists of nodes and edges of the graph, and the second element is a JSON object where the options for the layout are defined needs to be passed as a body of the request. Name field of the options body must be specified, other fields are optional. 
If user wants to provide ```width``` and ```height``` for each node individually, they should include them in the data object as in the samples below.

- [Sample JSON request body(width, height are included)](https://github.com/iVis-at-Bilkent/cytoscape-web-service/blob/master/public/samples/json_sample_width_height.json)

- [Sample JSON request body(simplest form)](https://github.com/iVis-at-Bilkent/cytoscape-web-service/blob/master/public/samples/sample4-compoundless-json.txt)

### SBGN-ML or GraphML:
First comes nodes and edges of the graph in either of two formats then the options body for the cytoscape.js in JSON.
- [Sample SBGN-ML request body](https://github.com/iVis-at-Bilkent/cytoscape-web-service/blob/master/public/samples/sample7-compoundless-sbgnml.txt)
- [Sample GraphML request body](https://github.com/iVis-at-Bilkent/cytoscape-web-service/blob/master/public/samples/sample1-compoundless-graphml.txt)


After the request is sent, the server will layout the given graph and return the JSON file with the node names and their positions.
If an error occurs, the response of the server will consist of the error's body.

## Compounds
Compounds are supported in graphml and json formats. Conventions for Cytoscape.js for compounds in graphml and json formats are supported by the web-server.

## Clusters
Clusters are supported in graphml and json formats. In json format clusterID field has to go to the data section of each node that has a cluster assigned to it. Similarly, in graphml clusterID key needs to be provided for each node that is part of some cluster.  

## Supported layouts
The supported layouts are:
- [fcose](https://github.com/iVis-at-Bilkent/cytoscape.js-fcose)
- [cose-bilkent](https://github.com/cytoscape/cytoscape.js-cose-bilkent)
- [cise](https://github.com/iVis-at-Bilkent/cytoscape.js-cise)
- [cose](https://github.com/iVis-at-Bilkent/cytoscape.js-cose)
- [dagre](https://github.com/cytoscape/cytoscape.js-dagre)
- [klay](https://github.com/cytoscape/cytoscape.js-klay)
- [avsdf](https://github.com/iVis-at-Bilkent/cytoscape.js-avsdf)
- [cola](https://github.com/cytoscape/cytoscape.js-cola)
- [euler](https://github.com/cytoscape/cytoscape.js-euler)
  
## Following is a list of third-party libraries used in building this web-service:
- [express](https://www.npmjs.com/package/express)
- [sbgnml-to-cytoscape](https://www.npmjs.com/package/sbgnml-to-cytoscape)
- [jsdom](https://www.npmjs.com/package/jsdom)
- [jQuery](https://www.npmjs.com/package/jquery)
- [cytoscape-graphml](https://www.npmjs.com/package/cytoscape-graphml)
- [cytoscape-fcose](https://www.npmjs.com/package/cytoscape-fcose)
- [cytoscape-cose-bilkent](https://www.npmjs.com/package/cytoscape-cose-bilkent)
- [cytoscape-dagre](https://www.npmjs.com/package/cytoscape-dagre)
- [cytoscape-klay](https://www.npmjs.com/package/cytoscape-klay)
- [cytoscape-avsdf](https://www.npmjs.com/package/cytoscape-avsdf)
- [cytoscape-cola](https://www.npmjs.com/package/cytoscape-cola)
- [cytoscape-euler](https://www.npmjs.com/package/cytoscape-euler)
- [cytoscape-spread](https://www.npmjs.com/package/cytoscape-spread)
- [cytoscape-cise](https://www.npmjs.com/package/cytoscape-cise)




 

 

