# Jointly Learning to Repair Code and Generate Commit Message #

---

We identify the task of **jointly learning to repair code and generate commit message**. To facilitate the study of this task, we construct  a  multilingual triple dataset including buggy code, fixed code, and commit messages. We collected data from [GitHub Archive](https://www.githubarchive.org/) using the GH Archive API. The collected raw data is released at [here](https://drive.google.com/file/d/1nv1UvlD0BigcObipg1sinowJ0ISaIO2j/view?usp=sharing). Apart from our collected multilingual dataset, we also build a Java-only monolingual triple dataset from the corpus (buggy-fixed pair) released by [Tufano et al. (2018)](https://dl.acm.org/doi/abs/10.1145/3340544), which can be found [here](https://sites.google.com/view/learning-fixes/data). 

The [processed data](https://drive.google.com/file/d/1k2S93O1szsYohJOr1nWbpxEP2Y7q3p3t/view?usp=sharing) is in the *dict* format. Each sample looks like the following:

	{"buggy": "def remove_appointment ( self , availability_id ) : <loc> self . cart_state . remove_appointment ( availability_id )",
	"fixed": "def remove_appointment ( self , availability_id ) : <loc> return self . cart_state . remove_appointment ( availability_id )",
	"diff": "def remove_appointment ( self , availability_id ) : <loc> <-> self . cart_state . remove_appointment ( availability_id ) <loc> <+> return self . cart_state . remove_appointment ( availability_id )",
	"message": "fix : add return value"}

| Key     | Description                                 |
| :---:     | :---                                      |
| buggy   | The method-level fragments with errors.     |
| fixed   | The repaired version of "buggy".            |
| diff    | The differences between "buggy" and "fixed". |
| message | The filtered commit message, indicating the changes from "buggy" to "fixed". |

- `<loc>` seperates each **physical** line of code. 

- `<->` denotes the line exists in `buggy` but not exists in `fixed`

- `<+>` denotes the line exists in `fixed` but not exists in `buggy`.

In progress ...





