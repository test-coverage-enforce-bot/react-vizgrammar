# React-VizGrammar

React VizGrammar is a wrapper around Victory JS and it makes charting easier by adding boilerplate code so that 
designers and developers can get started and set it up in a few minutes.

A chart can be embedded in a React environment simply by using the VizG react component.
```jsx
    import VizG from 'react-vizgrammar';

    <VizG config={config} data={data} metadata={metadata} />
``` 
where the props
- `config` is the widget configurations specified as a JSON object.
- `data` is the array of data sets fed to the charts.
- `metadata` is the JSON object that contains information about the provided dataset.

### Chart `config` prop
Users have to provide parameters for the widget using config object inorder to create the chart type they require. It is a JSON object that has a well defined configuration attributes to customize the chart.

Following is a basic configuration to plot a line chart,
```javascript
    let config = {
        x : "rpm",
        charts : [{type: "line",  y : "torque", color: "EngineType"}],
        maxLength: 10,
        width: 400,
        height: 200
    }
```
### `metadata` prop and `data` prop
Once the `config` is provided. User can provide a dataset to visualize the chart. For easy interpretation React-VizGrammar require this dataset to be arranged in a tabular way similar to the way explained below.
```javascript
    metadata = {
        "names": ["Column1", "Column2",...],
        "types": ['ordinal', 'linear',...]
    };
```

`metadata.names` is an array consists of column names/fields of the table and `metadata.types` contains their types 
(ordinal, time or linear), `names` and `types` are aligned together in a way that "Column1" => 'ordinal' and "Column2" => 'linear' and so on.

```javascript
    data = [
        ["value1", numericValue1,...],
        ["value2", numericValue2,...],
    ];
```
`data` collection of arrays of data rows. Single row is stored as an array and their element order follows the order of `metadata.names`.

Sample data table would be like following:
```javascript
    metadata = {
        "names" : ["rpm","torque","horsepower", "EngineType"],
        "types" : ["linear","linear", "ordinal","ordinal"]
    };

    data = [
        [8000, 75, 120, "Piston"], [9000, 81, 130, "Rotary"]
    ];
```

## Build Process

#### Prerequisites
- NPM
- Node 

These prerequisites must be installed before proceeding with the build process. 

#### Build the Library
In order build React-VizGrammar from the sources, Get a clone from this repository and then run the following commands in the terminal from the react-vizgrammar directory.
```bash
    npm install
    npm run build
```

#### Build and run samples
To build and start the dev-server and view the samples, inside the main directory run the following command afer installing the npm dependencies.
```bash
    npm run samples
```
