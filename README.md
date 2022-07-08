# UDEMY-WEB-DEVELOPMENT-COURSE-RATING-ANALYSIS
{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "5725d375",
   "metadata": {
    "papermill": {
     "duration": 0.01429,
     "end_time": "2021-11-18T00:10:05.942394",
     "exception": false,
     "start_time": "2021-11-18T00:10:05.928104",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "# **UDEMY WEB DEVELOPMENT COURSE RATING ANALYSIS**\n",
    "![](https://s.udemycdn.com/meta/default-meta-image-v2.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "5e5d7db8",
   "metadata": {
    "papermill": {
     "duration": 0.012624,
     "end_time": "2021-11-18T00:10:05.968450",
     "exception": false,
     "start_time": "2021-11-18T00:10:05.955826",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "**Context**\n",
    "This dataset is from Kaggle and it was scraped from Udemy. Udemy is one of the largest online course platforms, it provides all kinds courses to prepare for the ever-evolving future of work.\n",
    "\n",
    "Here we focused only on web development ratings.\n",
    "\n",
    "Dataset link: https://www.kaggle.com/nesreenalqahtani/udemy-dataset\n",
    "\n",
    "The scraped website link: https://www.udemy.com/courses/development/?p=1\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "dafa820c",
   "metadata": {
    "papermill": {
     "duration": 0.012562,
     "end_time": "2021-11-18T00:10:05.995968",
     "exception": false,
     "start_time": "2021-11-18T00:10:05.983406",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "\n",
    "| Field | Description |\n",
    "| :-- | :-- |\n",
    "| **Title** | title of course\n",
    "| **Instructor** | name of instructor\n",
    "| **Description** | content of course\n",
    "| **Rating** | rating of course (1-5 scale)\n",
    "| **User_vote** | Number of user voting\n",
    "| **Total_hours** | total of time of course\n",
    "| **Lecture** | Number of lectures\n",
    "| **Level** | level of complexity (Beginner, Intermediate, Expert, All levels)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "73d7f856",
   "metadata": {
    "papermill": {
     "duration": 0.012607,
     "end_time": "2021-11-18T00:10:06.021990",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.009383",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "# Downloading Dataset and Initial Observations"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "69f6e0e9",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.051839Z",
     "iopub.status.busy": "2021-11-18T00:10:06.050789Z",
     "iopub.status.idle": "2021-11-18T00:10:06.058159Z",
     "shell.execute_reply": "2021-11-18T00:10:06.058703Z",
     "shell.execute_reply.started": "2021-11-17T15:19:23.138795Z"
    },
    "papermill": {
     "duration": 0.024062,
     "end_time": "2021-11-18T00:10:06.059012",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.034950",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [],
   "source": [
    "import pandas as pd\n",
    "import matplotlib.pyplot as plt"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "91d72a3b",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.088693Z",
     "iopub.status.busy": "2021-11-18T00:10:06.088048Z",
     "iopub.status.idle": "2021-11-18T00:10:06.091338Z",
     "shell.execute_reply": "2021-11-18T00:10:06.091809Z",
     "shell.execute_reply.started": "2021-11-17T15:19:23.145950Z"
    },
    "papermill": {
     "duration": 0.019618,
     "end_time": "2021-11-18T00:10:06.091966",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.072348",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [],
   "source": [
    "pd.set_option('display.max_columns', 25)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "id": "20633959",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.122938Z",
     "iopub.status.busy": "2021-11-18T00:10:06.122305Z",
     "iopub.status.idle": "2021-11-18T00:10:06.216367Z",
     "shell.execute_reply": "2021-11-18T00:10:06.215811Z",
     "shell.execute_reply.started": "2021-11-17T15:19:23.160040Z"
    },
    "papermill": {
     "duration": 0.111526,
     "end_time": "2021-11-18T00:10:06.216532",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.105006",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [],
   "source": [
    "udemy  = pd.read_csv('../input/udemy-dataset/Udemy.csv')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "id": "f5a021ac",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.251812Z",
     "iopub.status.busy": "2021-11-18T00:10:06.250906Z",
     "iopub.status.idle": "2021-11-18T00:10:06.268015Z",
     "shell.execute_reply": "2021-11-18T00:10:06.268489Z",
     "shell.execute_reply.started": "2021-11-17T15:19:23.218310Z"
    },
    "papermill": {
     "duration": 0.039038,
     "end_time": "2021-11-18T00:10:06.268663",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.229625",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Title</th>\n",
       "      <th>Instructor</th>\n",
       "      <th>Description</th>\n",
       "      <th>Rating</th>\n",
       "      <th>User_vote</th>\n",
       "      <th>Total_hours</th>\n",
       "      <th>Lecture</th>\n",
       "      <th>Level</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Modern JavaScript From The Beginning</td>\n",
       "      <td>Brad Traversy</td>\n",
       "      <td>Learn and build projects with pure JavaScript ...</td>\n",
       "      <td>4.7</td>\n",
       "      <td>23409</td>\n",
       "      <td>21.5</td>\n",
       "      <td>122</td>\n",
       "      <td>All Levels</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Scrum Certification Prep PlusScrum MasterPlus ...</td>\n",
       "      <td>Paul Ashun</td>\n",
       "      <td>Overview of Scrum Agile project managementPlus...</td>\n",
       "      <td>4.4</td>\n",
       "      <td>22795</td>\n",
       "      <td>3.0</td>\n",
       "      <td>70</td>\n",
       "      <td>All Levels</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>NodeJS   The Complete Guide MVC  REST APIs  Gr...</td>\n",
       "      <td>Academind by Maximilian Schwarzm ller  Maximil...</td>\n",
       "      <td>Master Node JS and Deno js  build REST APIs wi...</td>\n",
       "      <td>4.7</td>\n",
       "      <td>22601</td>\n",
       "      <td>40.5</td>\n",
       "      <td>541</td>\n",
       "      <td>All Levels</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>The Complete Angular Course  Beginner to Advanced</td>\n",
       "      <td>Mosh Hamedani</td>\n",
       "      <td>The most comprehensive Angular 4  Angular 2Plu...</td>\n",
       "      <td>4.4</td>\n",
       "      <td>22477</td>\n",
       "      <td>29.5</td>\n",
       "      <td>376</td>\n",
       "      <td>All Levels</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>CHash Intermediate  Classes  Interfaces and OOP</td>\n",
       "      <td>Mosh Hamedani</td>\n",
       "      <td>An in depth  step by step guide to classes  in...</td>\n",
       "      <td>4.6</td>\n",
       "      <td>21967</td>\n",
       "      <td>6.0</td>\n",
       "      <td>45</td>\n",
       "      <td>Intermediate</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                                               Title  \\\n",
       "0               Modern JavaScript From The Beginning   \n",
       "1  Scrum Certification Prep PlusScrum MasterPlus ...   \n",
       "2  NodeJS   The Complete Guide MVC  REST APIs  Gr...   \n",
       "3  The Complete Angular Course  Beginner to Advanced   \n",
       "4    CHash Intermediate  Classes  Interfaces and OOP   \n",
       "\n",
       "                                          Instructor  \\\n",
       "0                                      Brad Traversy   \n",
       "1                                         Paul Ashun   \n",
       "2  Academind by Maximilian Schwarzm ller  Maximil...   \n",
       "3                                      Mosh Hamedani   \n",
       "4                                      Mosh Hamedani   \n",
       "\n",
       "                                         Description  Rating  User_vote  \\\n",
       "0  Learn and build projects with pure JavaScript ...     4.7      23409   \n",
       "1  Overview of Scrum Agile project managementPlus...     4.4      22795   \n",
       "2  Master Node JS and Deno js  build REST APIs wi...     4.7      22601   \n",
       "3  The most comprehensive Angular 4  Angular 2Plu...     4.4      22477   \n",
       "4  An in depth  step by step guide to classes  in...     4.6      21967   \n",
       "\n",
       "   Total_hours  Lecture         Level  \n",
       "0         21.5      122    All Levels  \n",
       "1          3.0       70    All Levels  \n",
       "2         40.5      541    All Levels  \n",
       "3         29.5      376    All Levels  \n",
       "4          6.0       45  Intermediate  "
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "udemy.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "id": "ee5114c8",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.299055Z",
     "iopub.status.busy": "2021-11-18T00:10:06.298441Z",
     "iopub.status.idle": "2021-11-18T00:10:06.328828Z",
     "shell.execute_reply": "2021-11-18T00:10:06.329376Z",
     "shell.execute_reply.started": "2021-11-17T15:19:23.230924Z"
    },
    "papermill": {
     "duration": 0.047136,
     "end_time": "2021-11-18T00:10:06.329534",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.282398",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Rating</th>\n",
       "      <th>User_vote</th>\n",
       "      <th>Total_hours</th>\n",
       "      <th>Lecture</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>9853.000000</td>\n",
       "      <td>9853.000000</td>\n",
       "      <td>9853.000000</td>\n",
       "      <td>9853.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>4.084807</td>\n",
       "      <td>468.375216</td>\n",
       "      <td>8.804933</td>\n",
       "      <td>64.279103</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>0.515485</td>\n",
       "      <td>1621.795070</td>\n",
       "      <td>11.660625</td>\n",
       "      <td>72.497594</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>1.200000</td>\n",
       "      <td>10.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>2.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>3.800000</td>\n",
       "      <td>27.000000</td>\n",
       "      <td>2.500000</td>\n",
       "      <td>24.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>4.200000</td>\n",
       "      <td>68.000000</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>42.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>4.500000</td>\n",
       "      <td>233.000000</td>\n",
       "      <td>10.000000</td>\n",
       "      <td>76.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>5.000000</td>\n",
       "      <td>23409.000000</td>\n",
       "      <td>173.500000</td>\n",
       "      <td>791.000000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            Rating     User_vote  Total_hours      Lecture\n",
       "count  9853.000000   9853.000000  9853.000000  9853.000000\n",
       "mean      4.084807    468.375216     8.804933    64.279103\n",
       "std       0.515485   1621.795070    11.660625    72.497594\n",
       "min       1.200000     10.000000     1.000000     2.000000\n",
       "25%       3.800000     27.000000     2.500000    24.000000\n",
       "50%       4.200000     68.000000     5.000000    42.000000\n",
       "75%       4.500000    233.000000    10.000000    76.000000\n",
       "max       5.000000  23409.000000   173.500000   791.000000"
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "udemy.describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "id": "804ea049",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.359899Z",
     "iopub.status.busy": "2021-11-18T00:10:06.359354Z",
     "iopub.status.idle": "2021-11-18T00:10:06.368244Z",
     "shell.execute_reply": "2021-11-18T00:10:06.368761Z",
     "shell.execute_reply.started": "2021-11-17T15:19:23.263040Z"
    },
    "papermill": {
     "duration": 0.025634,
     "end_time": "2021-11-18T00:10:06.368926",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.343292",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "udemy nulls: Title          0\n",
      "Instructor     0\n",
      "Description    0\n",
      "Rating         0\n",
      "User_vote      0\n",
      "Total_hours    0\n",
      "Lecture        0\n",
      "Level          0\n",
      "dtype: int64\n"
     ]
    }
   ],
   "source": [
    "print('udemy nulls:', udemy.isnull().sum())\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "id": "b31b07d3",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.400275Z",
     "iopub.status.busy": "2021-11-18T00:10:06.399704Z",
     "iopub.status.idle": "2021-11-18T00:10:06.404774Z",
     "shell.execute_reply": "2021-11-18T00:10:06.405306Z",
     "shell.execute_reply.started": "2021-11-17T15:19:23.278423Z"
    },
    "papermill": {
     "duration": 0.022429,
     "end_time": "2021-11-18T00:10:06.405486",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.383057",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Title           object\n",
      "Instructor      object\n",
      "Description     object\n",
      "Rating         float64\n",
      "User_vote        int64\n",
      "Total_hours    float64\n",
      "Lecture          int64\n",
      "Level           object\n",
      "dtype: object\n"
     ]
    }
   ],
   "source": [
    "print(udemy.dtypes)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "9b006d35",
   "metadata": {
    "papermill": {
     "duration": 0.014053,
     "end_time": "2021-11-18T00:10:06.433884",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.419831",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "# How many Instructors are included in this dataset?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "id": "be0eaa97",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.465749Z",
     "iopub.status.busy": "2021-11-18T00:10:06.465154Z",
     "iopub.status.idle": "2021-11-18T00:10:06.473009Z",
     "shell.execute_reply": "2021-11-18T00:10:06.472507Z",
     "shell.execute_reply.started": "2021-11-17T15:46:33.036388Z"
    },
    "papermill": {
     "duration": 0.024927,
     "end_time": "2021-11-18T00:10:06.473152",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.448225",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "1922\n"
     ]
    }
   ],
   "source": [
    "num_of_courses = udemy['Instructor'].value_counts()\n",
    "print(num_of_courses.unique().sum().sum())"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "5e3f9247",
   "metadata": {
    "papermill": {
     "duration": 0.014317,
     "end_time": "2021-11-18T00:10:06.502204",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.487887",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "# Which instuctor has the highest amount of courses?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "id": "2bb690ec",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.540276Z",
     "iopub.status.busy": "2021-11-18T00:10:06.533560Z",
     "iopub.status.idle": "2021-11-18T00:10:06.544246Z",
     "shell.execute_reply": "2021-11-18T00:10:06.543730Z",
     "shell.execute_reply.started": "2021-11-17T15:51:07.235282Z"
    },
    "papermill": {
     "duration": 0.027676,
     "end_time": "2021-11-18T00:10:06.544399",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.516723",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Instructor</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>name</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>Packt Publishing</th>\n",
       "      <td>606</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Laurence Svekis</th>\n",
       "      <td>174</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Bluelime Learning Solutions</th>\n",
       "      <td>173</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Eduonix Learning Solutions  Eduonix Tech</th>\n",
       "      <td>99</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Stone River eLearning</th>\n",
       "      <td>88</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Mammoth Interactive  John Bura</th>\n",
       "      <td>88</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Infinite Skills</th>\n",
       "      <td>84</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>John Elder</th>\n",
       "      <td>51</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Loony Corn</th>\n",
       "      <td>47</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Testing World</th>\n",
       "      <td>43</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>EDUmobile Academy</th>\n",
       "      <td>42</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Yohann Taieb</th>\n",
       "      <td>38</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Harshit Srivastava</th>\n",
       "      <td>35</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Sandeep Soni</th>\n",
       "      <td>30</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Pranjal Srivastava</th>\n",
       "      <td>30</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                                            Instructor\n",
       "name                                                  \n",
       "Packt Publishing                                   606\n",
       "Laurence Svekis                                    174\n",
       "Bluelime Learning Solutions                        173\n",
       "Eduonix Learning Solutions  Eduonix Tech            99\n",
       "Stone River eLearning                               88\n",
       "Mammoth Interactive  John Bura                      88\n",
       "Infinite Skills                                     84\n",
       "John Elder                                          51\n",
       "Loony Corn                                          47\n",
       "Testing World                                       43\n",
       "EDUmobile Academy                                   42\n",
       "Yohann Taieb                                        38\n",
       "Harshit Srivastava                                  35\n",
       "Sandeep Soni                                        30\n",
       "Pranjal Srivastava                                  30"
      ]
     },
     "execution_count": 9,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "course_count  = pd.DataFrame(num_of_courses).copy().head(15)\n",
    "course_count.index.name = 'name'\n",
    "\n",
    "course_count"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "id": "5f367b62",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:06.579616Z",
     "iopub.status.busy": "2021-11-18T00:10:06.578893Z",
     "iopub.status.idle": "2021-11-18T00:10:06.956987Z",
     "shell.execute_reply": "2021-11-18T00:10:06.956504Z",
     "shell.execute_reply.started": "2021-11-17T15:59:50.605890Z"
    },
    "papermill": {
     "duration": 0.397545,
     "end_time": "2021-11-18T00:10:06.957125",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.559580",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 792x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "\n",
    "course_count.plot(kind='barh', figsize=(11,6))\n",
    "plt.xlabel('# of Courses')\n",
    "plt.ylabel('Instructor Name')\n",
    "plt.title('Instructors with the Highest Amount of Courses');"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "6cd3a088",
   "metadata": {
    "papermill": {
     "duration": 0.016184,
     "end_time": "2021-11-18T00:10:06.989641",
     "exception": false,
     "start_time": "2021-11-18T00:10:06.973457",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "**Fun Fact: Packt Publishing has the most courses and the are leading by a landslide.Founded in 2004 in Birmingham, UK, Packt's mission is to help the world put software to work in new ways, through the delivery of effective learning and information services to IT professionals. They have published over 6,500 books and videos so far.**"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "bfe8391d",
   "metadata": {
    "papermill": {
     "duration": 0.015765,
     "end_time": "2021-11-18T00:10:07.021549",
     "exception": false,
     "start_time": "2021-11-18T00:10:07.005784",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "# Are there any trends between number of lectures and ratings of the course?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "id": "f233329b",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:07.059721Z",
     "iopub.status.busy": "2021-11-18T00:10:07.058740Z",
     "iopub.status.idle": "2021-11-18T00:10:07.346576Z",
     "shell.execute_reply": "2021-11-18T00:10:07.347046Z",
     "shell.execute_reply.started": "2021-11-17T16:00:56.356959Z"
    },
    "papermill": {
     "duration": 0.309633,
     "end_time": "2021-11-18T00:10:07.347206",
     "exception": false,
     "start_time": "2021-11-18T00:10:07.037573",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 936x576 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "udemy.plot(kind='scatter', x='Lecture', y='Rating', figsize=(13,8), s=2, c='green');\n",
    "plt.xlabel('# of Lectures')\n",
    "plt.ylabel('Course Rating')\n",
    "plt.title('# of Lectures by Course Rating');"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "ce9f20df",
   "metadata": {
    "papermill": {
     "duration": 0.016772,
     "end_time": "2021-11-18T00:10:07.381280",
     "exception": false,
     "start_time": "2021-11-18T00:10:07.364508",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "**The graph shows that there seems to be a positive trend between number of lectures and course ratings. It could be that courses with more lectures tend to go into more depth with each topic but we would need more data and in depth analysis to confirm that theory.**"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "0f087cd5",
   "metadata": {
    "papermill": {
     "duration": 0.016907,
     "end_time": "2021-11-18T00:10:07.415374",
     "exception": false,
     "start_time": "2021-11-18T00:10:07.398467",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "# Are there any trends between the total amount of hours and ratings of the course?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "id": "87b7f589",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:07.457417Z",
     "iopub.status.busy": "2021-11-18T00:10:07.454601Z",
     "iopub.status.idle": "2021-11-18T00:10:07.747803Z",
     "shell.execute_reply": "2021-11-18T00:10:07.748208Z",
     "shell.execute_reply.started": "2021-11-17T16:02:26.206166Z"
    },
    "papermill": {
     "duration": 0.315982,
     "end_time": "2021-11-18T00:10:07.748411",
     "exception": false,
     "start_time": "2021-11-18T00:10:07.432429",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 936x576 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "udemy.plot(kind='scatter', x='Total_hours', y='Rating', figsize=(13,8), s=2, c='green');\n",
    "plt.xlabel('Total Hours')\n",
    "plt.ylabel('Course Rating')\n",
    "plt.title('Total_hours by Course Rating');"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "6e790539",
   "metadata": {
    "papermill": {
     "duration": 0.018443,
     "end_time": "2021-11-18T00:10:07.785888",
     "exception": false,
     "start_time": "2021-11-18T00:10:07.767445",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "**The graph shows that there seems to be a positive trend between total hours and course ratings. Again, the courses could go into more depth or have more practice excercises and resources which causes the ratings to be higher.**"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "125fdfd9",
   "metadata": {
    "papermill": {
     "duration": 0.018086,
     "end_time": "2021-11-18T00:10:07.822268",
     "exception": false,
     "start_time": "2021-11-18T00:10:07.804182",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "# What are the average ratings per complexity level?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "id": "375e2e20",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2021-11-18T00:10:07.862550Z",
     "iopub.status.busy": "2021-11-18T00:10:07.861959Z",
     "iopub.status.idle": "2021-11-18T00:10:08.125306Z",
     "shell.execute_reply": "2021-11-18T00:10:08.124814Z",
     "shell.execute_reply.started": "2021-11-17T16:45:14.420056Z"
    },
    "papermill": {
     "duration": 0.284828,
     "end_time": "2021-11-18T00:10:08.125470",
     "exception": false,
     "start_time": "2021-11-18T00:10:07.840642",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 792x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "udemy_level = udemy[['Level', 'Rating']].groupby('Level').mean()\n",
    "udemy_level.plot(kind='bar', figsize=(11,6))\n",
    "plt.xlabel('Complexity Level')\n",
    "plt.ylabel('Course Rating')\n",
    "plt.title('Complexity Level by Course Rating');"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "c4800ef7",
   "metadata": {
    "papermill": {
     "duration": 0.018571,
     "end_time": "2021-11-18T00:10:08.166020",
     "exception": false,
     "start_time": "2021-11-18T00:10:08.147449",
     "status": "completed"
    },
    "tags": []
   },
   "source": [
    "**According to the graph expert has the lowest average ratings. This could be because expert level courses are typically judged more strictly. The could be to fast or to slow for the student. The instructor could also skip over that they feel the student should know. These are a couple out of potential reasons why average ratings may be lower for expert level courses.**\n",
    "\n",
    "# Conclusion\n",
    "**All and all it seems like students tend to be more satisfy with more optional material.**"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.10"
  },
  "papermill": {
   "default_parameters": {},
   "duration": 10.562179,
   "end_time": "2021-11-18T00:10:08.794486",
   "environment_variables": {},
   "exception": null,
   "input_path": "__notebook__.ipynb",
   "output_path": "__notebook__.ipynb",
   "parameters": {},
   "start_time": "2021-11-18T00:09:58.232307",
   "version": "2.3.3"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
