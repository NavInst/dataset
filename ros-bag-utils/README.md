# ROS Bag Utilities (`ros-bag-utils`)

`ros-bag-utils` is a collection of Python scripts/notebooks designed to help you efficiently process and manage ROS bag files. Whether you need to combine topics from multiple bags, extract specific topics, or handle image and PointCloud2 data, this toolkit provides the utilities to make your workflow smoother.

## Table of Contents
- [Installation](#installation)
- [Scripts Overview](#scripts-overview)
- [Contributing](#contributing)

## Installation

To use the scripts in this repository, you'll need Python with ROS Noetic is installed, along with the necessary dependencies for handling ROS bags. Ensure you have the following installed:

- `rosbag`
- `rospy`
- `numpy`
- `cv2` (OpenCV, for handling image data)
- `sensor_msgs` (specifically `point_cloud2` for handling PointCloud2 data)

## Scripts Overview

### `combine_topics_from_multiple_bags.ipynb`

This notebook enables you to merge specific topics from multiple ROS bag files into a single output bag, facilitating simultaneous analysis of data that is split across different bags.

To use this script, modify the following configuration in the notebook:
- **`main_path`**: Specify the directory where all your ROS bags are stored.
- **`bags_and_topics`**: Define a dictionary with each bag file as the key and a list of topics you want to merge from that bag.
- **`output_bag_path`**: Set the path for the newly created merged bag file.

### `extract_topics_from_bag.ipynb`

This notebook is a general-purpose utility for extracting any topics from a ROS bag and saving them in CSV format. It is particularly useful for converting ROS message data into a more accessible format for analysis or integration into other workflows.

To use this script, modify the following configuration in the notebook:
- **`bag_file`**: Specify the path to the ROS bag file you want to extract data from.
- **`topics`**: List the topics you wish to extract from the bag. Each topic's data will be saved in a separate CSV file.
- **`out_folder`**: Define the directory where the CSV files will be saved. The script will automatically create a CSV file for each topic listed.


### `extract_image_topics_from_bag.ipynb`

This notebook extracts image topics from a ROS bag and saves the images as files, making it particularly useful for visualizing or processing image data outside of ROS.

To use this script, modify the following configuration in the notebook:

- **`bag_file`**: Specify the path to the ROS bag file that contains the image topics you want to extract.
- **`topics`**: List the image topics you wish to extract from the bag. The script will create a separate folder for each topic.
- **`out_folder`**: Define the directory where the output folders and images will be saved. Each topic will have its own subfolder.

For each topic, the script creates:

1. **A Subfolder**: Named based on the topic.
2. **`metadata.csv` File**: Inside each subfolder, this CSV file holds the ROS message information for each image, such as the timestamp and other relevant metadata.
3. **`images/` Subfolder**: Inside this folder, each image message is saved as a `.jpg` file, named according to its timestamp.

#### Example Folder Structure:

For a topic `/oak/image_raw_color/compressed`, the folder structure would look like this:
```bash
oak_image_raw_color_compressed/
├── metadata.csv  # Contains ROS message metadata like timestamp, sequence, frame ID, and filename.
└── images/
    ├── [NANOSECOND_UNIX_TIME_1].jpg
    ├── [NANOSECOND_UNIX_TIME_2].jpg
    ├── ...
```

### `extract_pointcloud2_topics_from_bags.ipynb`

This notebook extracts `PointCloud2` topics from a ROS bag and saves the points as files in either `.csv` or `.pcd` formats. It is particularly useful for visualizing point clouds using software such as CloudCompare or for processing outside of ROS.

To use this script, modify the following configuration in the notebook:

- **`bag_file`**: Specify the path to the ROS bag file that contains the `PointCloud2` topics you want to extract.
- **`topics`**: List the `PointCloud2` topics you wish to extract from the bag. The script will create a separate folder for each topic.
- **`out_folder`**: Define the directory where the output folders and point cloud files will be saved. Each topic will have its own subfolder.
- **`OUT_CHOICE`**: Choose the output file format for the point clouds. You can select between `OutputFormat.PCD` for ASCII PCD files or `OutputFormat.CSV` for Comma Separated Values files.

For each topic, the script creates:

1. **A Subfolder**: Named based on the topic.
2. **`csv_metadata.csv` or `pcd_metadata.csv` File**: Inside each subfolder, this CSV file holds metadata related to the ROS messages, including the timestamp and other relevant details.
3. **`csv_pointclouds/` or `pcd_pointclouds/` Subfolder**: Inside this folder, each `PointCloud2` message is saved as a `.csv` or `.pcd` file, named according to its timestamp.

#### Example Folder Structure:

For a topic `/velodyne/lidar/points`, if `OUT_CHOICE` is set to `OutputFormat.PCD`, the folder structure would look like this:
```bash
velodyne_lidar_points/
├── pcd_metadata.csv  # Contains ROS message metadata like timestamp and sequence information.
└── pcd_pointclouds/
    ├── [NANOSECOND_UNIX_TIME_1].pcd
    ├── [NANOSECOND_UNIX_TIME_2].pcd
    ├── ...
```







## Contributing
Contributions are welcome! If you have improvements, bug fixes, or additional utilities to add, please fork the repository, make your changes, and submit a pull request.


