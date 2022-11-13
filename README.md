# CoursePlanner
CICS CoursePlanner intends to be a smart tool to help empower students choose courses geared towards their interests. 

# Features

1. Planning Ahead: Make sure you get the prerequites satisfied for future courses
2. Focus your Degree: Indicate your interests to take the courses that matter most
3. Informed Decisions: Easy access to RateMyProfessor reviews for every course

# Concept
<html>
    <head>
        <meta charset="utf-8">     
            <script src="lib/bindings/utils.js"></script>
            <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/vis-network/9.1.2/dist/dist/vis-network.min.css" integrity="sha512-WgxfT5LWjfszlPHXRmBWHkV2eceiWTOBvrKCNbdgDYTHrT2AeLCGbF4sZlZw3UMN3WtL0tGUoIAKsu8mllg/XA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
            <script src="https://cdnjs.cloudflare.com/ajax/libs/vis-network/9.1.2/dist/vis-network.min.js" integrity="sha512-LnvoEWDFrqGHlHmDD2101OrLcbsfkrzoSpvtSQtxK3RMnRV0eOkhhBN2dXHKRrUU8p2DGRTk35n4O8nWSVe1mQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<center>
<h1></h1>
</center>
<!-- <link rel="stylesheet" href="../node_modules/vis/dist/vis.min.css" type="text/css" />
<script type="text/javascript" src="../node_modules/vis/dist/vis.js"> </script>-->
        <link
          href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css"
          rel="stylesheet"
          integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6"
          crossorigin="anonymous"
        />
        <script
          src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/js/bootstrap.bundle.min.js"
          integrity="sha384-JEW9xMcG8R+pH31jmWH6WWP0WintQrMb4s7ZOdauHnUtxwoG2vI5DkLtS3qm9Ekf"
          crossorigin="anonymous"
        ></script>
        <center>
          <h1></h1>
        </center>
        <style type="text/css">
             #mynetwork {
                 width: 250px;
                 height: 250px;
                 background-color: #ffffff;
                 border: 1px solid lightgray;
                 position: relative;
                 float: left;
             }
        </style>
    </head>
    <body>
        <div class="card" style="width: 100%">
            <div id="mynetwork" class="card-body"></div>
        </div>
        <script type="text/javascript">
              // initialize global variables.
              var edges;
              var nodes;
              var allNodes;
              var allEdges;
              var nodeColors;
              var originalNodes;
              var network;
              var container;
              var options, data;
              var filter = {
                  item : '',
                  property : '',
                  value : []
              };
              // This method is responsible for drawing the graph, returns the drawn network
              function drawGraph() {
                  var container = document.getElementById('mynetwork');
                  // parsing and collecting nodes and edges from the python
                  nodes = new vis.DataSet([{"color": "#97c2fc", "id": "220", "label": "220", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "326", "label": "326", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "383", "label": "383", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "305", "label": "305", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "320", "label": "320", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "187", "label": "187", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "230", "label": "230", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "240", "label": "240", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "250", "label": "250", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "311", "label": "311", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "121", "label": "121", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "198C", "label": "198C", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "365", "label": "365", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "453", "label": "453", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "446", "label": "446", "shape": "dot", "size": 10}, {"color": "#97c2fc", "id": "466", "label": "466", "shape": "dot", "size": 10}]);
                  edges = new vis.DataSet([{"arrows": "to", "from": "220", "to": "326", "width": 1}, {"arrows": "to", "from": "220", "to": "383", "width": 1}, {"arrows": "to", "from": "220", "to": "305", "width": 1}, {"arrows": "to", "from": "220", "to": "320", "width": 1}, {"arrows": "to", "from": "187", "to": "220", "width": 1}, {"arrows": "to", "from": "187", "to": "230", "width": 1}, {"arrows": "to", "from": "187", "to": "240", "width": 1}, {"arrows": "to", "from": "187", "to": "250", "width": 1}, {"arrows": "to", "from": "187", "to": "311", "width": 1}, {"arrows": "to", "from": "121", "to": "187", "width": 1}, {"arrows": "to", "from": "121", "to": "198C", "width": 1}, {"arrows": "to", "from": "230", "to": "365", "width": 1}, {"arrows": "to", "from": "230", "to": "305", "width": 1}, {"arrows": "to", "from": "230", "to": "453", "width": 1}, {"arrows": "to", "from": "198C", "to": "230", "width": 1}, {"arrows": "to", "from": "240", "to": "383", "width": 1}, {"arrows": "to", "from": "240", "to": "305", "width": 1}, {"arrows": "to", "from": "240", "to": "446", "width": 1}, {"arrows": "to", "from": "250", "to": "311", "width": 1}, {"arrows": "to", "from": "250", "to": "305", "width": 1}, {"arrows": "to", "from": "311", "to": "466", "width": 1}, {"arrows": "to", "from": "383", "to": "446", "width": 1}]);
                  nodeColors = {};
                  allNodes = nodes.get({ returnType: "Object" });
                  for (nodeId in allNodes) {
                    nodeColors[nodeId] = allNodes[nodeId].color;
                  }
                  allEdges = edges.get({ returnType: "Object" });
                  // adding nodes and edges to the graph
                  data = {nodes: nodes, edges: edges};
                  var options = {
    "configure": {
        "enabled": false
    },
    "edges": {
        "color": {
            "inherit": true
        },
        "smooth": {
            "enabled": true,
            "type": "dynamic"
        }
    },
    "interaction": {
        "dragNodes": true,
        "hideEdgesOnDrag": false,
        "hideNodesOnDrag": false
    },
    "physics": {
        "enabled": true,
        "stabilization": {
            "enabled": true,
            "fit": true,
            "iterations": 1000,
            "onlyDynamicEdges": false,
            "updateInterval": 50
        }
    }
};
                  network = new vis.Network(container, data, options);
                  return network;
              }
              drawGraph();
        </script>
    </body>
</html>

The project highly emphasizes algorithms with graph theory. We used the following process:
1. Integrate with school systems to get course information
2. Build a network graph that represents pre-requsite to course mapping
3. Interface with RateMyProfessor API to calculate course ratings
4. And surely a lot of algos to develop an optimal course path!

# Demo
<link>

# Tech Stack
- ![React Frontend Website]()
- ![Fast API Python Backend]()
# 

# Special Thanks
- Spire API: https://spire-api.melanson.dev/
- CICS Consultant: https://cics-consultant.herokuapp.com/html/fields.html (for course categories)