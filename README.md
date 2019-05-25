# vue-gaugejs-gallery

<strong>What is this project? :</strong>

- The vue-gaugejs-gallery project is a collection of gauges from gaugeJS that can be used in vue projects.
- You can customize any of the gauges as you would shown in the demo for gaugeJS (link listed below).
- The "test component" and "test gauge" are just an example of how you would implement the gauge as a reusable component 
  where the value of gaugeScore is passed down from props.

<br>

<strong>Setting up a cloned repo of this project :</strong>

- Requires: gaugeJS, Bootstrap, Vue.js
- To install gaugeJS you can install the node package with (npm i gaugeJS). Link for reference https://www.npmjs.com/package/gaugeJS.
- To run the application use (npm run serve).

<br>

<strong>Customizing your gauges :</strong>

  <br>
  
  gaugeScore :
  
- gaugeScore is what determines the value for the graph and can be passed down from another component.
- The value for gaugeScore determines the length of the bar for the gauge and the animated number that is generated (if there is one).
- If you like you can take other data objects from "opts" and put them into props.
  
  <table>
    <tr>
      <th>Type</th>
      <th>Name</th>
      <th>Value</th>
      <th>Explanation</th>
    </tr>
    <tr>
      <td>Props</td>
      <td>gaugeScore</td>
      <td>35</td>
      <td>Sets the value of the gauge to 35</td>
    </tr>
  </table>
  
  <br>
  
  opts :
  
- opts is used as a data object that contains all of the relevant features for styling the gauge.
- The value for gaugeScore determines the length of the bar for the gauge and the animated number that is generated (if there is one).
- If you like you can take other data objects from "opts" and put them into props.
  
  <table>
    <tr>
      <th>Type</th>
      <th>Name</th>
      <th>Value</th>
      <th>Explanation</th>
    </tr>
  
    <tr>
      <td>Data</td>
      <td>angle</td>
      <td>0.1</td>
      <td>Sets the gauge angle (for example half circle or full circle)</td>
    </tr>
    
    <tr>
      <td>Data</td>
      <td>lineWidth</td>
      <td>0.44</td>
      <td>Sets the thickiness of the gauge</td>
    </tr>
    
    <tr>
      <td>Data</td>
      <td>radiusScale</td>
      <td>1</td>
      <td>Sets the radius of the gauge</td>
    </tr>
  </table>
  
  <br>
  
  pointer :
  
- Part of "opts" data object.
- Controls appearance of the point in the gauge.
  
  <table>
    <tr>
      <th>Type</th>
      <th>Name</th>
      <th>Value</th>
      <th>Explanation</th>
    </tr>
  
    <tr>
      <td>Data</td>
      <td>length</td>
      <td>0.6</td>
      <td>Sets the length for the pointer</td>
    </tr>
    
    <tr>
      <td>Data</td>
      <td>strokeWidth</td>
      <td>0.035</td>
      <td>Sets the thickiness of the pointer</td>
    </tr>
    
    <tr>
      <td>Data</td>
      <td>color</td>
      <td>"#000000"</td>
      <td>Sets the color for the pointer</td>
    </tr>
  </table>
  
  <br>

<strong>Source :</strong>

- gaugeJS https://bernii.github.io/gauge.js/#!
