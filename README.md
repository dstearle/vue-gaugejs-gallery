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

- Props: gaugeScore is what determines the value for the graph and can be passed down from another component. If you like you can take
  other values from data and put them into props.
  
  <table>
    <tr>
      <td>Props</td>
      <td>gaugeScore</td>
      <td>35</td>
      <td>Sets the value of the gauge to 35</td>
    </tr>
  </table>

<br>

<strong>Source:</strong>

- gaugeJS https://bernii.github.io/gauge.js/#!
