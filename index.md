---
layout: default
title: BlendMimic3D Dataset
github_repo: "https://github.com/FilipaLino/BlendMimic3D"
download_zip: "https://drive.google.com/uc?export=download&id=1lToowcVOqQx6-d8CLdarpyB7tiYftyQC"
---

<p align="center">
  <img src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/Blendmimic3DOccl2.png" alt="Subjects" width="100%" />
</p>

# Introduction 
---
In response to the escalating demand for detailed datasets for human pose estimation (HPE), we introduce the **BlendMimic3D Dataset**. By providing a synthetic dataset that bridges the realism gap in current HPE datasets, BlendMimic3D stands as a pivotal tool for advancing pose estimation technologies. Its creation not only demonstrates the potential of synthetic datasets to enhance algorithm training and testing but also sets a new benchmark for dataset complexity and utility in the HPE domain.

### Motivation

Traditional datasets for HPE, while invaluable, often fall short in replicating the complex, occlusion-heavy environments encountered in real-world applications. The Human3.6M dataset, despite its contributions to the field, exemplifies these limitations. Utilizing Blender, a leading open-source 3D computer graphics software, we've crafted BlendMimic3D to specifically address these gaps, offering a diverse array of scenarios that range from simple, controlled settings to intricate, occlusion-rich environments.

### Integration with GCN Pose Refinement

Our development of the BlendMimic3D dataset was significantly inspired by advancements in pose refinement techniques, particularly through the use of Graph Convolutional Networks (GCN). The [**GCN Pose Refinement Block**](./GCN-page.html) represents a cornerstone of our approach, enhancing the accuracy of pose estimation in occluded scenarios. By training our GCN on the BlendMimic3D dataset, we've achieved notable improvements in pose estimation fidelity, especially in complex occlusion contexts. 

### Dataset Composition

BlendMimic3D is meticulously constructed with the following components:

- **Scenarios**: From simple to complex, including extensive occlusion challenges.
- **Subjects**: Three distinct subjects, each performing a variety of actions.
- **Actions**: Each subject engages in 14 unique actions, captured across single and multi-person setups.
- **Videos**: The dataset encompasses 128 videos, each with a duration of approximately 20 seconds (600 frames).

<p align="center">
  <img src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/subjects.png" alt="Subjects" width="70%" />
</p>

### Technological Backbone

The dataset's creation involved positioning four cameras within a virtual environment to capture a full spectrum of movements. Characters, animated via resources from Mixamo, engage in a range of actions from arguing to greeting, with their 3D poses meticulously extracted and analyzed.

<div style="display: flex; justify-content: center; align-items: center;">
    <video width="70%"  controls >
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/Dataset-Data.mp4" type="video/mp4">
    </video>
</div>


### Key Features

- **Adaptability**: BlendMimic3D's design ensures its relevance and applicability across various occlusion scenarios and HPE models.
- **Comprehensive Metadata**: Accompanying each video is detailed metadata, including camera calibration parameters and the 2D and 3D positions of keypoints.

### Videos
#### S1
<div style="display: flex; justify-content: left; align-items: center; gap: 20px;">
    <video width="30%" controls>
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/Reactions_1.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <video width="30%" controls>
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/SittingCheering_2.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>

#### S2
<div style="display: flex; justify-content: left; align-items: center; gap: 20px;">
    <video width="30%" controls>
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/StandingArguing_0.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <video width="30%" controls>
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/ShoppingBag_3.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>

#### S3
<div style="display: flex; justify-content: left; align-items: center; gap: 20px;">
    <video width="45%" controls>
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/Focus_3.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <video width="45%" controls>
        <source src="https://raw.githubusercontent.com/FilipaLino/filipalino.github.io/main/images/Focus_multi_2.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>




[Next Page](./GCN-page.html).

