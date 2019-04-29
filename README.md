# RaGOO-in-cwl
Wrapper tool of [RaGOO](https://github.com/malonge/RaGOO) by [CWL](https://github.com/common-workflow-language/common-workflow-language) and [Docker](https://www.docker.com)

## Requirements

* cwl-runner such as [cwltool](https://github.com/common-workflow-language/cwltool)
* Docker
    * If you cannot use docker, this tool runs with `--no-container` options.
    * However, you have to install dependent tools of RaGOO, such as python3, intervaltree, numpy, and minimap2


## How to use

With the [CWL reference implementation](https://github.com/common-workflow-language/cwltool/) (`cwltool`), [`toil-cwl-runner`](https://toil.readthedocs.io/en/latest/running/cwl.html), or [`arvados-cwl-runner`](https://dev.arvados.org/projects/arvados/wiki/Running_Common_Workflow_Language_%28CWL%29_workflows_on_Arvados) as your `cwl-runner`:

```
cwl-runner --outdir ${PATH_TO_OUTPUT_DIR} \
           ragoo.cwl \
           --contigs_fasta ${PATH_TO_CONTIG_FILE} \
           --reference_fasta  ${PATH_TO_REFERENCE_FILE} \
```

For other runners an input object is required:
> inputs.yml
```
contigs_fasta:
  class: File
  path: path/to/file
reference_fasta:
  class: File
  path: path/to/other/file
```

```
cwl-runner --outdir ${PATH_TO_OUTPUT_DIR} \
           ragoo.cwl \
           inputs.yml
```

## Note

As the original RaGOO implementation cannot handle with absolute file path, this tool uses [modified version](https://github.com/TaskeHAMANO/RaGOO) in the container.
