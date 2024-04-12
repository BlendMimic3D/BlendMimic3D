---
layout: default
title: Pose Refinement with GCN
github_repo: "https://github.com/FilipaLino/GCN-Pose-Refinement"
description: A "plug-and-play" solution, adapting to various 3D HPE frameworks without requiring training them.
---

## Overview
We introduce our Graph Convolutional Network (GCN) as a plugin to enhance the estimated 3D poses. Our GCN is trained on the BlendMimic3D dataset, which provides a diverse range of occlusion scenarios. This allows the network to learn and adapt to various occlusion types, refining the pose estimation for occluded joints. 

<div style="display: flex; align-items: center; justify-content: space-between; max-width: 100%;">
    <div style="margin-right: 10px; width: 60%;">
        <p>Our graph dynamics model considers six classes as neighboring nodes for each keypoint:</p>
        <ol>
            <li>Center (red)</li>
            <li>Physically-connected node closer to the spine (blue)</li>
            <li>Physically-connected farther from the spine (green)</li>
            <li>Symmetric node (pink)</li>
            <li>Time-forward node (orange)</li>
            <li>Time-backward (yellow)</li>
        </ol>
    </div>
    <div style="width: 350px;">
        <img src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/GCN_gif.gif" alt="Illustration of the graph dynamics" style="width: 100%; height: auto;">
    </div>
</div>

## Results
Our results show the significant impact of the GCN block compared to previous methods in occlusion scenarios, as evidenced by the BlendMimic3D results. Below, we provide an overview of both CPN-based and Detectron2-based detections, utilizing the Human3.6M and BlendMimic3D test sets. 

<style>
    /* Base table styles */
    table {
        border-collapse: separate;
        border-spacing: 0;
        width: 100%;
        border-radius: 8px;
        overflow: hidden; /* Ensures the border radius applies by hiding overflow */
        box-shadow: 0 4px 8px rgba(0,0,0,0.1); /* Subtle shadow around the table */
        margin-top: 20px; /* Adds some spacing above the table */
    }

    th, td {
        padding: 12px; /* Increased padding for better spacing */
        text-align: left;
        border-bottom: 1px solid #ccc; /* Light border for rows */
    }

    th {
        background-color: #b2b2b2; /* A more vibrant header color */
        color: #ffffff; /* White text for contrast */
    }

    /* Alternating row colors */
    tr:nth-child(even) {
        background-color: #f2f2f2;
    }

    /* Last row border fix */
    tr:last-child td {
        border-bottom: none;
    }

    /* First column styling */
    td:first-child, th:first-child {
        border-right: 2px solid #ccc; /* Adds a defining border to separate the first column */
    }
</style>
<div style="overflow-x:auto;">
    <table>
        <tr>
            <td rowspan="1"></td>
            <td></td>
            <th colspan="2" style="text-align:center"><b>Human3.6M<p>(Avg ± σ [mm])</p></b></th>
            <th colspan="2" style="text-align:center"><b>BlendMimic3D<p>(Avg ± σ [mm])</p></b></th>
        </tr>
        <tr>
            <th style="text-align:left"><b>Model</b></th>
            <th><b>2D HPE</b></th>
            <th><b>MPJPE</b></th>
            <th><b>P-MPJPE</b></th>
            <th><b>MPJPE</b></th>
            <th><b>P-MPJPE</b></th>
        </tr>
        <tr>
            <td>VideoPose3D</td>
            <td>CPN</td>
            <td><b>47.8 ± 9.29</b></td>
            <td><b>37.4 ± 7.10</b></td>
            <td>175.0 ± 7.20</td>
            <td>112.0 ± 8.42</td>
        </tr>
        <tr>
            <td>+ GCN</td>
            <td>CPN</td>
            <td>56.3 ± 9.33</td>
            <td>42.4 ± 7.06</td>
            <td><b>112.7 ± 6.76</b></td>
            <td><b>87.2 ± 5.29</b></td>
        </tr>
        <tr>
            <td>VideoPose3D</td>
            <td>Detectron2</td>
            <td><b>57.3 ± 9.96</b></td>
            <td><b>43.6 ± 8.14</b></td>
            <td>198.0 ± 7.88</td>
            <td>122.5 ± 3.67</td>
        </tr>
        <tr>
            <td>+ GCN</td>
            <td>Detectron2</td>
            <td>59.7 ± 10.35</td>
            <td>44.1 ± 8.08</td>
            <td><b>127.7 ± 11.42</b></td>
            <td><b>95.8 ± 6.90</b></td>
        </tr>
        <tr>
            <td>PoseFormerV2</td>
            <td>CPN</td>
            <td><b>46.0 ± 9.08</b></td>
            <td><b>36.4 ± 7.05</b></td>
            <td>148.6 ± 8.00</td>
            <td>107.7 ± 5.78</td>
        </tr>
        <tr>
            <td>+ GCN</td>
            <td>CPN</td>
            <td>49.6 ± 9.85</td>
            <td>37.3 ± 7.16</td>
            <td><b>107.5 ± 2.03</b></td>
            <td><b>81.6 ± 4.76</b></td>
        </tr>
        <tr>
            <td>PoseFormerV2</td>
            <td>Detectron2</td>
            <td>76.5 ± 19.97</td>
            <td>55.6 ± 11.97</td>
            <td>155.0 ± 9.35</td>
            <td>112.2 ± 7.90</td>
        </tr>
        <tr>
            <td>+ GCN</td>
            <td>Detectron2</td>
            <td><b>60.9 ± 11.55</b></td>
            <td><b>44.6 ± 9.29</b></td>
            <td><b>106.9 ± 8.13</b></td>
            <td><b>76.5 ± 7.04</b></td>
        </tr>
        <tr>
            <td>D3DP</td>
            <td>CPN</td>
            <td><b>41.4 ± 8.19</b></td>
            <td><b>33.2 ± 6.42</b></td>
            <td>100.7 ± 7.94</td>
            <td>79.0 ± 5.88</td>
        </tr>
        <tr>
            <td>+ GCN</td>
            <td>CPN</td>
            <td>56.2 ± 7.20</td>
            <td>40.9 ± 6.22</td>
            <td><b>95.3 ± 3.58</b></td>
            <td><b>72.1 ± 4.09</b></td>
        </tr>
        <tr>
            <td>D3DP</td>
            <td>Detectron2</td>
            <td><b>51.9 ± 7.79</b></td>
            <td><b>40.3 ± 7.01</b></td>
            <td>99.9 ± 11.19</td>
            <td>79.6 ± 8.08</td>
        </tr>
        <tr>
            <td>+ GCN</td>
            <td>Detectron2</td>
            <td>58.7 ± 7.75</td>
            <td>42.1 ± 6.89</td>
            <td><b>95.3 ± 4.86</b></td>
            <td><b>74.3 ± 4.50</b></td>
        </tr>
    </table>
</div>

### Qualitative Results

<div style="display: flex; justify-content: center; align-items: center;">
    <video width="100%"  controls >
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/Results/JLo.mp4" type="video/mp4">
    </video>
</div>

<div style="display: flex; justify-content: center; align-items: center;">
    <video width="100%"  controls >
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/Results/TakeItem_multi.mp4" type="video/mp4">
    </video>
</div>

 
[Back](./)
