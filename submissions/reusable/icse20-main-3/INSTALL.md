The data is collected from Stack Overflow and GitHub and then labeled manually as described in the Methodology section in our paper. The data has been uploaded in this repository with the name `Dataset.xlsx`.
- The dataset spreadsheet contains two sheets named `Stack Overflow` and `GitHub` that store the deep learning bugs collected from Stack Overflow and GitHub of five libraries (Caffe, Keras, Tensorflow, Theano, and Torch), respectively. Each file has five columns, which are bug, the bug fix pattern from a prior study [20], bug fix pattern, library, and bug type. The first column, bug, stores the Stack Overflow posts and GitHub commits, which contains deep learning bugs. The second column, bug fix pattern from a prior study, is the labels of bug fix pattern based on the prior study. However, these labels are applied to traditional programs, which are not suitable for Deep learning programs. Thus, we have created new appropriate labels for deep learning software. The third column, bug fix pattern, is the new bug fix pattern labels for DNN bugs. The fourth column, library, shows which library the bug belongs. The final column, bug type represents the types of deep learning bugs that are created from a prior study.

- The dataset spreadsheet contains two sheets named `Fig1a` and `Fig1b` that show the bug fix pattern distribution of Stack Overflow and GitHub of five deep learning libraries, respectively. Each file contains a table with two columns. The first column presents the types of bug fix pattrns. The second column shows the distribution of the bug fix pattern in five libraries.

- The dataset spreadsheet contains a sheet named `Table3` that indicates the percentage of each bug fix pattern of each deep learning library. SO and GH columns are the percentage of bug fix patterns of Stack Overflow and GitHub, respectively.

- The dataset spreadsheet contains two sheets named `Fig2` and `Fig3` that show the distribution of bug fix patterns for different bug types of Stack Overflow and GitHub, respectively.

- The dataset spreadsheet contains a sheet named `Fig6+Table5` that shows the distribution of the new bugs across the different libraries and how these new bugs are classified into different categories of bug type, root cause, and impact.

- The dataset spreadsheet contains a sheet named `Table6` that presents the changes of Tensorflow APIs in different versions. The first column shows the operators of Tensorflow APIs in the latest version, version 2. The remaining columns show the names of these operators in the previous versions which include 1.14, 1.13, 1.12, 1.11, 1.1.