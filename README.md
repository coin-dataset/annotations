# COIN Dataset

> [COIN](https://coin-dataset.github.io/) is the currently largest dataset for comprehensive instruction video analysis. It contains 11,827 videos of 180 different tasks (i.e., car polishing, make French fries) related to 12 domains (i.e., vehicle, dish). All videos are collected from YouTube and annotated with an efficient [toolbox](https://github.com/coin-dataset/annotation-tool).


## Authors and Contributors
<p>
Yansong Tang<sup>*</sup>, Dajun Ding<sup>†</sup>, Yongming Rao<sup>*</sup>, Yu Zheng<sup>*</sup>, Danyang Zhang<sup>*</sup>, Lili Zhao<sup>†</sup>, Jiwen Lu<sup>*</sup>, Jie Zhou<sup>*</sup>, Yongxiang Lian<sup>*</sup>, Yao Li<sup>†</sup>, Jiali Sun<sup>†</sup>, Chang Liu<sup>†</sup>, Dongge You<sup>†</sup>, Zirun Yang<sup>†</sup>, Jiaojiao Ge<sup>†</sup>, Jiayun Wang<sup>*</sup>
</p>

- <sup>*</sup>Tsinghua University
- <sup>†</sup>Meitu Inc.

**Contact:** [coin.dataset@gmail.com](mailto:coin.dataset@gmail.com)

## License
You may use the codes and files for research only, including sharing and modifying the material. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

## Dataset and Annotation

### Taxonomy

The COIN is organized in a hierarchical structure, which contains three levels: `domain`, `task` and `step`. The corresponding relationship can be found at taxonomy [link]. We provide the taxonomy file of COIN in csv format. Below, we show a small part of the texonomy stored in [`taxonomy.xlsx`](taxonomy.xlsx): 

<table>
<tr><th>domain_target_mapping </th><th>target_action_mapping</th></tr>
<tr><td><table></table>

| Domains             | Targets                      | 
| ------------------- | ---------------------------- |
| ...		      | ...			     |
| Vehicle             | ChangeCarTire		     |
| Vehicle	      | InstallLicensePlateFrame     |
| ...		      | ...			     |
| Gadgets	      | ReplaceCDDriveWithSSD	     |

</td><td>


| Target Id           | Target Label                 | Action Id             | Action Label  		|   
| ------------------- | ---------------------------- | --------------------- | ------------------------ |		
| ...		      | ...			     | ...		     | ...		  	|
| 13                  | ChangeCarTire		     | 259		     | unscrew the screw        |
| 13	              | ChangeCarTire                | 260		     | jack up the car		|
| 13		      | ChangeCarTire	             | 261		     | remove the tire          |
| 13	      	      | ChangeCarTire	 	     | 262		     | put on the tire          |
| 13	      	      | ChangeCarTire	     	     | 263		     | tighten the screws	|
| ...		      | ...			     | ...		     | ...			|

</td></tr> </table>

We store the url of video and their annotation in JSON format, which can be accessed with the link [COIN](Project link page). The json file is similar to that of [ActivityNet](http://activity-net.org/download.html). Below, we show an example entry from the key field "database":

```
"LtRSn-ntcLY": {
			"duration": 131.0309,
			"class": "ReplaceCDDriveWithSSD",
			"video_url": "https://www.youtube.com/embed/LtRSn-ntcLY",
			"start": 56.640895694775196,
			"annotation": [
				{
					"id": "212",
					"segment": [
						60.0,
						69.0
					],
					"label": "take out the laptop CD drive"
				},
				{
					"id": "216",
					"segment": [
						71.0,
						82.0
					],
					"label": "insert the hard disk tray into the position of the CD drive"
				}
			],
			"subset": "training",
			"end": 85.714362947023,
			"recipe_type": 131
		}
```
From the entry, we can easily retrieve the Youtube ID, duration, ROI and procedure information of the video. The field "annotation" comprises of a list of all annotated procedures within the video. The field "class" and sub-field "id" correspond to "task" and "step" of the taxonomy respectively.

### File Structure

The annotation information is saved in [`COIN.json`](COIN.json).

| Field Name          | Type                         | Example          | Description                                                                                                           |
| ------------------- | ---------------------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------- |
| `database`          | string                          | -             | Key filed of the annotation file.                                                                                             |
| -                   | string                       | `LtRSn-ntcLY`         | Youtube ID of the video.                                                                                              |
| `duration`          | float                        | 56.640895694775196   | Duration of the video in seconds.                                                        |
| `class`             | string                       | `ReplaceCDDriveWithSSD`   | Name of the task in the video.                                                                           |
| `video_url`    | string                       | `https://www.youtube.com/embed/LtRSn-ntcLY`   | Url of the video.                                                                             |
| `start`       | float                          | 56.640895694775196          | Start time of the ROI of the video. |
| `end`        | float                          | 85.714362947023          | End time of the ROI of the video.  |
| `subset`    | string                       | `training` or `validation`           | Subset of the video.                                                                                                |
| `recipe_type`              | int                       | 131          | ID number of the task.                                                                                       |
| `annotation`              | string                       | -        | Annotation information of the video.                                                                                 |
| `annotation`:`id`        | int                          | 212              | ID number of the procedure.                                                                                |
| `annotation`:`label`       | string                          | `take out the laptop CD drive`             | Name of the procedure.                                                                                |
| `annotation`:`segment`         | list of float (len=2)   | `[60.0,69.0]`     | Start and end time of the procedure.                                                                          |

