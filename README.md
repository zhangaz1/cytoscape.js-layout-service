# cytoscape-web-service
Web-service on cytoscape.js to layout graphs

Deployed at:
https://cytoscape-layout-service.herokuapp.com/

This web-server supports 3 input formats for graphs:
1. sbgnml
2. graphml
3. json

In order to layout any graph, POST request to the: https://cytoscape-layout-service.herokuapp.com/layout/:file_format needs to be send, and the type of the request must be 'text' or 'text/plain'.

The format of the request is:
an array where the first element of the array will also be an array that will consist of nodes and edges of the graph, and the second element will be JSON object where the options for the layout will be specified. Name field of the layout must be specified, while other fields are optional.

After the request is sent, the server will layout the given graph and return the JSON file with the node names and their positions.
If an error occurs, the response of the server will consist of the error's body.

