# GroupDocs.Total for Python via .NET - Code Examples

[GroupDocs.Total for Python via .NET](https://products.groupdocs.com/total/python-net/) is a metapackage: one command installs the 14 GroupDocs for Python via .NET products, each a self-contained wheel with its own .NET runtime.

```bash
pip install groupdocs-total-net
```

The 14 product wheels download about 2.2 GB and take about 3.2 GB on disk. Python 3.5 to 3.14 on Windows x64, Linux x86_64 (glibc 2.27 or later) and macOS 13 or later, on Intel and Apple Silicon.

## Examples for each product

Every product keeps its runnable examples in its own repository:

| Product | Package | Examples |
|---|---|---|
| GroupDocs.Conversion | `groupdocs-conversion-net` | [GroupDocs.Conversion-for-Python-via-.NET](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Python-via-.NET) |
| GroupDocs.Viewer | `groupdocs-viewer-net` | [GroupDocs.Viewer-for-Python-via-.NET](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Python-via-.NET) |
| GroupDocs.Comparison | `groupdocs-comparison-net` | [GroupDocs.Comparison-for-Python-via-.NET](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Python-via-.NET) |
| GroupDocs.Watermark | `groupdocs-watermark-net` | [GroupDocs.Watermark-for-Python-via-.NET](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Python-via-.NET) |
| GroupDocs.Metadata | `groupdocs-metadata-net` | [GroupDocs.Metadata-for-Python-via-.NET](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Python-via-.NET) |
| GroupDocs.Merger | `groupdocs-merger-net` | [GroupDocs.Merger-for-Python-via-.NET](https://github.com/groupdocs-merger/GroupDocs.Merger-for-Python-via-.NET) |
| GroupDocs.Assembly | `groupdocs-assembly-net` | [GroupDocs.Assembly-for-Python-via-.NET](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Python-via-.NET) |
| GroupDocs.Redaction | `groupdocs-redaction-net` | [GroupDocs.Redaction-for-Python-via-.NET](https://github.com/groupdocs-redaction/GroupDocs.Redaction-for-Python-via-.NET) |
| GroupDocs.Signature | `groupdocs-signature-net` | [GroupDocs.Signature-for-Python-via-.NET](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Python-via-.NET) |
| GroupDocs.Parser | `groupdocs-parser-net` | [GroupDocs.Parser-for-Python-via-.NET](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Python-via-.NET) |
| GroupDocs.Search | `groupdocs-search-net` | [GroupDocs.Search-for-Python-via-.NET](https://github.com/groupdocs-search/GroupDocs.Search-for-Python-via-.NET) |
| GroupDocs.Annotation | `groupdocs-annotation-net` | [GroupDocs.Annotation-for-Python-via-.NET](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Python-via-.NET) |
| GroupDocs.Editor | `groupdocs-editor-net` | [GroupDocs.Editor-for-Python-via-.NET](https://github.com/groupdocs-editor/GroupDocs.Editor-for-Python-via-.NET) |
| GroupDocs.Markdown | `groupdocs-markdown-net` | [GroupDocs.Markdown-for-Python-via-.NET](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-Python-via-.NET) |

## Using several products in one script

Import each product from its own package. Products can be combined in one Python process; on Windows, set `DOTNET_MULTILEVEL_LOOKUP` to `0` at the top of the script, before the first call into any product:

```python
import os

os.environ["DOTNET_MULTILEVEL_LOOKUP"] = "0"  # Windows: every product keeps its own .NET runtime

from groupdocs.conversion import Converter
from groupdocs.conversion.options.convert import PdfConvertOptions
from groupdocs.watermark import Watermarker
from groupdocs.watermark.watermarks import TextWatermark, Font

with Converter("document.docx") as converter:
    converter.convert("document.pdf", PdfConvertOptions())

with Watermarker("document.pdf") as watermarker:
    watermarker.add(TextWatermark("CONFIDENTIAL", Font("Arial", 36.0)))
    watermarker.save("watermarked.pdf")
```

Without the setting, on a Windows machine with a newer .NET installed system-wide, Viewer, Metadata, Annotation, Comparison, Editor, Merger and Redaction load that runtime instead of their own, and the second of them in one process fails with `RuntimeError: hostfxr_get_runtime_delegate failed with 0x800080a3`.

## Licensing

Without a licence every product runs in evaluation mode. Set `GROUPDOCS_LIC_PATH` to a GroupDocs.Total licence file or URL once, and each product applies it at its first call; or call `License().set_license(path)` from the product you use.

## Resources

- [Documentation](https://docs.groupdocs.com/total/python-net/)
- [Release notes](https://releases.groupdocs.com/total/python-net/release-notes/)
- [PyPI package](https://pypi.org/project/groupdocs-total-net/)
- [Free Support Forum](https://forum.groupdocs.com/c/total/8)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
