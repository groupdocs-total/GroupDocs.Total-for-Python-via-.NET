# AGENTS.md

Guidance for AI agents (and people) working with this repository.

## What this is

The entry point for Python code examples of GroupDocs.Total for Python via .NET, the `groupdocs-total-net` metapackage on PyPI. The metapackage installs the 14 GroupDocs for Python via .NET products and holds no code; the runnable examples live in each product's own examples repository, listed in `README.md`.

## Facts to rely on

- Install: `pip install groupdocs-total-net`. About 2.2 GB to download and 3.2 GB on disk.
- Python 3.5 to 3.14; Windows x64, Linux x86_64 with glibc 2.27 or later, macOS 13 or later (Intel and Apple Silicon).
- Linux needs ICU (`libicu`); several products also use `libgdiplus`, `fontconfig` and fonts.
- Import each product from its own package: `groupdocs.conversion`, `groupdocs.viewer`, `groupdocs.comparison`, `groupdocs.watermark`, `groupdocs.metadata`, `groupdocs.merger`, `groupdocs.assembly`, `groupdocs.redaction`, `groupdocs.signature`, `groupdocs.parser`, `groupdocs.search`, `groupdocs.annotation`, `groupdocs.editor`, `groupdocs.markdown`. There is no `groupdocs.total` module.
- Licensing is per product: `GROUPDOCS_LIC_PATH` (a licence file path or URL) covers every product at its first call; otherwise call `License().set_license(path)` from each product used.

## Writing code that uses several products

- Products can share one Python process. On Windows, put `os.environ["DOTNET_MULTILEVEL_LOOKUP"] = "0"` at the top of the script, before the first call into any product. Without it, on a machine with a newer .NET installed system-wide, the second of Viewer, Metadata, Annotation, Comparison, Editor, Merger or Redaction in one process fails with `RuntimeError: hostfxr_get_runtime_delegate failed with 0x800080a3`.
- Uninstalling one product removes the shared `groupdocs/pydrawing` module from the others. `pip install --force-reinstall --no-deps groupdocs-viewer-net==26.9.0` restores it.

## Links

- Documentation: https://docs.groupdocs.com/total/python-net/
- Release notes: https://releases.groupdocs.com/total/python-net/release-notes/
- PyPI: https://pypi.org/project/groupdocs-total-net/
- Support forum: https://forum.groupdocs.com/c/total/8
