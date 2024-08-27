# navinst.dataset

The `navinst.dataset` repository is a collection of tools and utilities designed to help you work efficiently with the NavINST dataset ROS bags. 


## Table of Contents
- [Instructions](#instructions)
- [Overview](#overview)
- [The Dataset](#the-dataset)
- [Contributing](#contributing)
- [License](#license)


## Instructions

This repository is tested and validated with ROS1 Noetic on Ubuntu 20.04.

Ensure you have ROS Noetic installed and your catkin workspace configured. Detailed instructions for setting up and using the tools in this repository are provided in the README files within each subfolder.

## Overview
This repository is divided into the following subfolders:
- **`navinst_ros`**: Contains a ROS package with custom message definitions essential for working with specific topics in the NavINST dataset.
- **`ros_bag_utils`**: Provides a variety of scripts and tools for processing and managing ROS bag files. These tools can be used with any ROS bag files, and not limited to the NavINST dataset.
- **`visualization`**: Provides data visualization capabilties, helping users to better interpret the NavINST dataset.


## The Dataset

The NavINST dataset can be accessed at [https://navinst.github.io/](https://navinst.github.io/).

If you use our work or the dataset in your research, please cite our paper:

```bibtex
@article{navinst2024,
  author    = {Author Name and Another Author},
  title     = {Title of the Paper},
  journal   = {Journal Name},
  year      = {2024},
  volume    = {12},
  number    = {34},
  pages     = {567-589},
  doi       = {10.1234/journalname.2024.56789},
}
```


## Contributing
Contributions are welcome! If you have improvements, bug fixes, or additional utilities to add, please fork the repository, make your changes, and submit a pull request.

## License

This repository is licensed under the MIT License. See the [LICENSE.md](./LICENSE.md) file for more information.
