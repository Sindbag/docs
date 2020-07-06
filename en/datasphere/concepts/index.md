# About {{ ml-platform-name }}

{{ ml-platform-full-name }} is a machine learning (ML) development environment that combines the familiar Jupyter® Notebook interface, serverless computing technology, and seamless use of different computing resource configurations. {{ ml-platform-full-name }} helps significantly reduce the cost of machine learning compared to computing on your own hardware or other cloud platforms.

If you never used Jupyter Notebook, try it: notebooks are convenient as they help you execute code sequentially and immediately visualize the results. Notebooks are also convenient for making analytical reports and articles: you can add explanations between the code cells in [Markdown](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html).

## Advantages of the service {#advantages}

### A ready-to-use development environment {#ready-to-use}

You don't need to spend time creating and maintaining VMs: when you create a new [project](project.md), computing resources are automatically allocated for implementing it.

The VM comes ready with the JupyterLab development environment and pre-installed packages for data analysis and ML (such as TensorFlow, Keras, and NumPy), which you can start using immediately. The full list of [pre-installed packages](preinstalled-packages.md).

If you're missing a package, you can [install it](../operations/projects/install-dependencies.md) right from the notebook.

### Automatic maintenance of computing resources {#auto-service}

The service automatically manages resource allocation. If you don't perform any computations, no resources are allocated.

### Saving the state when shutting down {#save-state}

If you close the notebook tab, the state of the interpreter, all variables, and computation results are saved. You can continue working when you reopen your project.

{% include [include](../../_includes/datasphere/saving-variables-warn.md) %}

### Managing computing resources {#control-computing-resources}

Different computing resources are required for different tasks. For some of them, a regular processor is enough, but for others, you need a GPU.

{{ ml-platform-name }} supports different computing resource [configurations](configurations.md). By default, projects run with the minimal <q>S</q> configuration (32 GB RAM and 2 vCPUs).

You can [change the configuration](../operations/projects/control-compute-resources.md) at any time when working in the notebook. The state of the interpreter is maintained.

### Errors don't change the state of the interpreter {#handling-errors}

If an error occurs while running a cell, it won't update the state of the interpreter. This allows you to keep the results obtained in the previous cells.

{% note warning %}

If a variable value was assigned in the cell where the error occurred, the assignment is also canceled.

{% endnote %}

### You can share your results {#share-results}

You can [export your notebook to HTML format](../operations/projects/share.md) with all calculation results and cell explanations and share a link to the report in this format. Exporting in other formats is currently not supported.

## Current limitations of the service {#known-restrictions}

For more information about service limits, see [{#T}](limits.md).

#### See also {#see-also}

* [{#T}](../operations/index.md)
* [{#T}](limits.md)
* [{#T}](../pricing.md)
