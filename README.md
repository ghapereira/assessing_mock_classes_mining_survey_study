# Assessing Mock Classes: A Mining and Survey Study

## Objective

This repository contains the data extracted from 12 open-source projects regarding Java classes, and also anonimized data related to a survey on mock classes usage.

## Description

### Mining study (file classes_analysis_data.csv)

The data is contained in a text file separated by semicolons (';').
Each row describes the features of a single Java class. It has fifteen columns:

* **ProjectName**: String representing the project's name, stated as its name on GitHub

* **Filename**: String representing the name (path) of the file that contains the class

* **Classname**: String representing the name of the class

* **LOC**: Integer representing the number of code lines of the class

* **Visibility**: Indicates the Java visibility of the class (`private`, `protected`, `package` or `public`)

* **IsMock**: Boolean (`True` or `False`) representing whether the class is classified as mock class by the paper's heuristic or not

* **Extensions**: Integer (`0` or `1`) representing how many classes the current one extends

* **Implementations**: Integer (`0+`) representing how many interfaces the current classs implements

* **PrivateMethods**: Integer (`0+`) representing how many private methods the class have

* **ProtectedMethods**: Integer (`0+`) representing how many protected methods the class have

* **PackageMethods**: Integer (`0+`) representing how many package methods the class have

* **PublicMethods**: Integer (`0+`) representing how many public methods the class have

* **TotalMethods**: Integer (`0+`) representing how many methods in total the class have regardless of their visibilities

* **IsStaticClass**: Boolean (`True` or `False`) representing whether the class is or not static

* **MethodOverrides**: Integer (`0+`) representing how many of the class' methods are overriding others

### Evolutionary data (RQ3)

To answer the research question _How are mock classes modified along a project history?_ data on the original 12 projects history was obtained. This data is present on the file **mock_evolutionary.csv**. The baseline data to be compared, which are randomly selected non-mock classes from the same projects, is on the file **baseline_evolutionary.csv**. One can notice that there is one more line on the mock file than on the baseline one; it is due to a single mock class in a project which is not statistically relevant, so the line was not searched for in the baseline.

The columns present on the file are:

* **project**: String representing the project's name, stated as its name on GitHub
* **file**: String representing the name (path) of the file that contains the class
* **class**: String representing the name of the class
* **changes**: Integer representing the number of changes of the class, obtained by counting the commits in which it was changed
* **distinct_authors**: Integer representing the count of distinct authors that have modified (e.g. commited a revision) the class

### Survey (file SurveyAnswers.ods)

The data is contained in a [ODS file](https://www.iso.org/standard/66363.html), which can be opened by open-source applications such as [LibreOffice](https://www.libreoffice.org/), or commercial desktop/online applications. This is also a format supported by open-source software libraries such as [Pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/io.html). Each row represents one answer from a developer that answered our survey. The answers are anonimized, and any information on the e-mail answer that was not integral to the survey purposes was scrubbed, such as greetings or personal information related items.

Missing data is handled by leaving the cell only with a "-" symbol. For the categories attributes, multiple categories are possible for any given answer, so multiple categories are separated by a comma ",".

The columns present in the file are:

* **developer_id**: Integer representing an unique identifier number for each developer/answer. One can notice that not all numbers between 1 and 45 were present. These "missing" numbers are those answers that did not contain information deemed relevant for answering any of the questions, so they were omitted.

* **commit_count**: Integer representing the count of commits made by the user in its respective project, found by counting the number of commits under its e-mail address. In some cases it was identified multiple e-mails for the same person, and whenever these were found they were aggregated into one. Missing data in this column means that the developer that answered has no commits in their e-mail address on the project - it happened when a developer forwarded an e-mail to a different one that made the change but for a number of reasons did not had its e-mail address attached to commits.

* **project**: String representing the project's name, stated as its name on GitHub

* **answer**: String containing the scrubbed answer to the survey questions

* **categories_q1**: String containing the categorization by the authors on how the developer message answers the first survey question (_What is the goal of this mock class?_)

* **categories_q2**: String containing the categorization by the authors on how the developer message answers the second survey question (_Why has a mocking framework (eg. Mockito) not been used instead?_)

* **categories_q3**: String containing the categorization by the authors on how the developer message answers the third survey question (_Based on your experience, when should developers create mock classes and when should they rely on mocking frameworks?_)
