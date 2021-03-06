# plot.py

Uses plotly to visualize text files (tab, space, comma separated or any content that has a structure) or pickled pandas dataframes. A lot of features are supported like reading in files with different separators, selecting and sorting columns, processing of multiple files, plotting line, scatter, bar, violin, box and gantt charts and customizing the graphs to all the needs.

This script acts as a master script generating a plotting script. In case this script doesn't cover something that is required for a graph, it can output the final plotting script to make manual adjustments like adding annotations.

## Requirements

PIP3 packages:
* plotly
* numpy
* pandas
* colour

```
pip3 install plotly numpy pandas colour
```

Download the latest plotly-orca at https://github.com/plotly/orca/releases. Script will search for these executables by default:
* /opt/plotly-orca/orca
* /opt/plotly/orca
* orca

An executable defined with the environment variable `PLOTLY_ORCA` takes
precedence. You can also define the orca binary as an argument to plot.py.

**Plotly requires a special orca version which is incompatible with the
original orca!**

## Examples

#### Line Chart
```
plot.py -i lines.csv --plot line --output line.png
```
![Line Chart](/plots/line.png)
#### Scatter Chart
```
plot.py -i scatter.csv --plot line --line-mode markers --output scatter.png
```
![Scatter Chart](/plots/scatter.png)
#### Bar Chart
```
plot.py -i bar.csv --plot bar --output bar.png
```
![Bar Chart](/plots/bar.png)
#### Box Chart
```
plot.py -i distribution.csv --plot box --output box.png
```
![Box Chart](/plots/box.png)
#### Violin Chart
```
plot.py -i distribution.csv --plot violin --output violin.png
```
![Violin Chart](/plots/violin.png)
#### Gantt Chart
```
plot.py -i gantt.csv --plot bar --bar-mode stack --bar-text-position inside --orientation h --x-type date --output gantt.png
```
![Gantt Chart](/plots/gantt.png)
```
plot.py -i gantt_time.csv --plot bar --bar-mode stack --bar-text-position outside --orientation h --x-type date --output gantt_time.png
```
![Gantt Time Chart](/plots/gantt_time.png)
#### Combined Subplots
```
plot.py -i lines.csv --colspan 2 -i scatter.csv --row 2 --colspan 1 --line-mode markers -i bar.csv --col 2 --plot bar -i distribution.csv --row 3 --col 1 --plot violin -i distribution.csv --col 2 --plot box --horizontal-spacing 0.05 --vertical-spacing 0.05 --per-trace-colours --output subplot.png
```
![Subplot Chart](/plots/subplots.png)

# numprops.py

Calculates number properties of the number set passed via paramters or from stdin. Filters any numbers from the given input and can combine number sets given via paramter and stdin. Adjustable precision and POSIX friendly output. Supports the the following properties: count, sum, minimum, maximum, average, median(q2), q1, q3, any percentile (p%), standard deviation, variance and p-value statistics (by providing a second number set).

### Requirements

PIP3 packages:
* numpy
* scipy

### Examples

```
> cat /proc/cpuinfo | grep MHz | numprops.py
Count                Sum      Min      Max                 Q2        Avg                  σ
   12 45696.465000000004 3781.705 3912.226 3787.1270000000004 3808.03875 43.673346303599956

> cat /proc/cpuinfo | grep MHz | numprops.py --precision 2 -p min max avg p99
    Min     Max     Avg     P99
2444.84 3604.36 3173.42 3590.52
```
