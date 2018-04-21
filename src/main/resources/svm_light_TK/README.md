# Tree Kernels in SVM-light

## Installation

1. [Download the source code](http://disi.unitn.it/moschitti/Tree-Kernel.htm).
2. Decompress and make (Assume you downloaded v1.5)
    ```shell
    cd /path/to/dir/of/svm-light-TK-1.5.zip
    unzip svm-light-TK-1.5.zip
    cd SVM-Light-1.5-to-be-released
    make
    ```
3. Copy the binary files to this directory
    ```shell
    cp svm_learn /path/to/this/directory
    cp svm_classify /path/to/this/directory
    ```


## Note

`svm_classify` with version `V5.01-TK-1.5` raised some errors in my environment and I modified `svm_common.c` as follows.

```diff
371,374c371,374
<   /* if(strcmp(version_buffer,VERSION)) { */
<   /*   perror ("Version of model-file does not match version of svm_classify!");  */
<   /*   exit (1);  */
<   /* } */
---
>   if(strcmp(version_buffer,VERSION)) {
>     perror ("Version of model-file does not match version of svm_classify!"); 
>     exit (1); 
>   }
391c391
<   /* fscanf(modelfl,"%ld%*[^\n]\n", &model->kernel_parm.tree_kernel_params); */
---
>   fscanf(modelfl,"%ld%*[^\n]\n", &model->kernel_parm.tree_kernel_params);
397d396
<   printf("totwords=%d\n", model->totwords);
```
