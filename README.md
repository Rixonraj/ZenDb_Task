# ZenDb_Task

Collections:
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/87fa75e9-9733-41e4-a517-31ef23071a1a)

zenclass.Attendance Collection

![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/1d8c7313-e9c3-40ef-99dc-bc705d920ae3)

zenclass
.CodeKata Collection

![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/c135fe8b-32a5-4ebc-919b-c98c9838e4ed)

zenclass.Company drive Collection

![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/eb60ea4a-2da7-482d-a44d-f6099e6472a9)

zenclass.Mentor Collection
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/880b4c3e-d464-402b-bb48-3064fbf1985b)

zenclass.Task collection
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/18f7b030-b26b-42d0-b5a3-c3262609dfed)

zenclass.Topics Collection
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/8b91d0ff-2ea5-4770-ae27-0513aea32694)

zenclass.User Collection
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/9bb71d30-f50c-4ca8-85ba-13efcbd81ae6)

Find all the topics and tasks which are thought in the month of October

[
  {
    $lookup: {
      from: "Task collection",
      localField: "Date",
      foreignField: "Date",
      as: "Tasks",
    },
  },
  {
    $project: {
      Date1: {
        $month: "$Date",
      },
      topicName: 1,
      Date: 1,
      Tasks: {
        taskName: 1,
      },
    },
  },
  {
    $project: {
      topicName: 1,
      Date1: 1,
      Date: 1,
      Tasks: {
        $cond: {
          if: {
            $eq: [[], "$Tasks"],
          },
          then: "$$REMOVE",
          else: "$Tasks",
        },
      },
    },
  },
  {
    $unwind: {
      path: "$Tasks",
      preserveNullAndEmptyArrays: true,
    },
  },
  {
    $project: {
      topicName: 1,
      Date: 1,
      Date1: 1,
      task: "$Tasks.taskName",
    },
  },
  {
    $match: {
      Date1: {
        $eq: 10,
      },
    },
  },
]

![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/690cac0c-e41b-4c49-85cd-14a594703fc3)

Find all the company drives which appeared between 15 oct-2020 and 31-oct-2020
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/72b061a7-396a-4826-9acb-3a9ec976cec7)


Find all the company drives and students who are appeared for the placement.
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/63fb0440-8013-4fda-99b3-3e4aad494061)

Find the number of problems solved by the user in codekata
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/87feb920-e425-4d74-8fdb-1d342956777c)

Find all the mentors with who has the mentee's count more than 15
![image](https://github.com/Rixonraj/ZenDb_Task/assets/85862632/cf9b8aaf-f344-4414-8c10-53e00c93d5e9)

