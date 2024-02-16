# Labelme2YOLOv8

**Forked from[ [greatv/labelme2yolo]([https://github.com/rooneysh/Labelme2YOLO](https://github.com/greatv/labelme2yolo))](https://github.com/greatv/labelme2yolo)**

[![PyPI - Version](https://img.shields.io/pypi/v/labelme2yolov8.svg)](https://pypi.org/project/labelme2yolov8)

Labelme2YOLOv8 is a powerful tool for converting LabelMe's JSON dataset Yolov8 format. This tool can also be used for YOLOv5/YOLOv8 segmentation datasets, if you have already made your segmentation dataset with LabelMe, it is easy to use this tool to help convert to YOLO format dataset.

## New Features

* export data as yolo polygon annotation (for YOLOv8 segmentation)
* Existing Structure (YOLOv5 v7.0)

+ YOLODataset
    + images
        + test
        + train
        + val
    + labels
        + test
        + train
        + val
		
* Updated Structure (YOLOv8)

+ YOLOv8Dataset
    + test
        + images
        + labels
    + train
        + images

        + labels
    + val
        + images
        + labels


## Installation

```shell
pip install labelme2yolov8
```

## Arguments

**--json\_dir** LabelMe JSON files folder path.

**--val\_size (Optional)** Validation dataset size, for example 0.2 means 20% for validation.

**--test\_size (Optional)** Test dataset size, for example 0.2 means 20% for Test.

**--json\_name (Optional)** Convert single LabelMe JSON file.

**--output\_format (Optional)** The output format of label.

**--label\_list (Optional)** The pre-assigned category labels.

## How to Use

### 1. Converting JSON files and splitting training, validation, and test datasets with --val\_size and --test\_size

You may need to place all LabelMe JSON files under **labelme\_json\_dir** and then run the following command:

```shell
labelme2yolov8 --json_dir /path/to/labelme_json_dir/ --val_size 0.15 --test_size 0.15
```

This tool will generate dataset labels and images with YOLO format in different folders, such as

```plaintext
/path/to/labelme_json_dir/YOLOv8Dataset/train/labels/
/path/to/labelme_json_dir/YOLOv8Dataset/test/labels/
/path/to/labelme_json_dir/YOLOv8Dataset/val/labels/
/path/to/labelme_json_dir/YOLOv8Dataset/train/images/
/path/to/labelme_json_dir/YOLOv8Dataset/test/images/
/path/to/labelme_json_dir/YOLOv8Dataset/val/images/

/path/to/labelme_json_dir/YOLOv8Dataset/dataset.yaml
```

### 2. Converting JSON files and splitting training and validation datasets by folders

If you have split the LabelMe training dataset and validation dataset on your own, please put these folders under **labelme\_json\_dir** as shown below:

```plaintext
/path/to/labelme_json_dir/train/
/path/to/labelme_json_dir/val/
```

This tool will read the training and validation datasets by folder. You may run the following command to do this:

```shell
labelme2yolov8 --json_dir /path/to/labelme_json_dir/
```

This tool will generate dataset labels and images with YOLO format in different folders, such as

```plaintext
/path/to/labelme_json_dir/YOLOv8Dataset/train/labels/
/path/to/labelme_json_dir/YOLOv8Dataset/val/labels/
/path/to/labelme_json_dir/YOLOv8Dataset/train/images/
/path/to/labelme_json_dir/YOLOv8Dataset/val/images/

/path/to/labelme_json_dir/YOLOv8Dataset/dataset.yaml
```

## How to build package/wheel

1. [install hatch](https://hatch.pypa.io/latest/install/)
2. Run the following command:

```shell
hatch build
```

## License

`labelme2yolov8` is distributed under the terms of the [MIT](https://spdx.org/licenses/MIT.html) license.
