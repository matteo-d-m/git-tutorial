# What is Git, and Why Use It?
Scientific data analysis can be complex, especially for people that divide their time between different projects. The _conceptual_ complexity of the scientific task adds to the _technical_ complexity of implementing it in a given programming language, which in turn implies preparing and using some computing set-up. If you multiply this complexity for all the projects that you might work on at a given time, things can get out of hand quickly.  

Beside being complex, scientific data analysis tends to be _iterative_ &mdash; that is, it unfolds over a sequence of steps where you continuously try and fail new approaches, progressively adding useful features and removing useless ones from your code. 

One way to handle this complexity is to keep changes explainable and tracked &mdash; that is, to create and use a method that can help users find their way across the data analysis process. 

Traditionally, people have pursued explainability with _logbooks_ and _multiplication_: 

- _Logbooks_ are written documents that summarise the steps taken to carry out a given analysis. Often, logbooks are intended for the private use of the scientist who carries out the analysis. As such, they are usually written with paper and pencil, they are separate from the actual code, they are unaccessible to anyone who wishes to understand the analysis from the outside, and they can easily get lost during events like a transfer from one workplace to another
- _Multiplication_ refers to the practice of multiplying code files to keep track of their versions, inserting information about the version in the filename. For example, the first version of a TMS-EEG preprocessing pipeline can reside in a file named `pipeline_v1.py`, the second in a file named `pipeline_v2.py`, the third in a file named `pipeline_v3.py`, etc. 

While they can be effective for projects that are small and short, logbooks and multiplication have three unforgivable flaws that make them unfit for larger, longer projects:

1. **Scale.** Given the number of attempts that are usually required to go from first to last attempt, multiplication can result in a huge number of files and a correspondingly huge number of entries in a logbook. To avoid having too many files and notes for the same pipeline, people often choose to save only the most meaningful versions, at risk of losing track of some modifications and the exact impact they had on the pipeline
2. **Dispersion.** Logbooks and multiplication tend to disperse information across different media: if we multiply code files and write the reasons in a logbook, the actual modification lives in an entirely different place than the explanation, as the multiplied files live in the computer and the logbook most likely lives in a physical drawer. Even if the logbook is digital, it lives in a different file than the code it refers to &mdash; perhaps even in a different directory
3. **Lack of transparency.** While the final version of a code file has some chances of being published at the end of a project, past versions and logbooks usually rest in a private archive forever. This is a huge limitation in cases when reconstructing the genesis of some code matters &mdash; for example, when someone finds a bug and needs to understand how it came to be
4. **Lack of standard.** There is no universal naming convention for code files, nor for writing logbooks. While seemingly trivial, this is a concrete obstacle on the way to clarity and transparency

The alternative to logbooks and multiplication is to work on a single file and keep track of its different versions in-place using a standardised system like Git:

> [!IMPORTANT]
> Git is a version control system (VCS) &mdash; that is, a software to keep track of the modifications made to other software.

The name Git is often found in conjunction with GitHub. But, what is GitHub?

> [!IMPORTANT]
> GitHub is two things:
> 1. A web service that relies on Git to allow multiple users to collaborate on one project while keeping track of everyone's actions
> 2. A platform for sharing code and the associated version history with the general public