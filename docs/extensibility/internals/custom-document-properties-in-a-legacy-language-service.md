---
title: Benutzerdefinierte Dokumenteigenschaften in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b3db7f4cfa45ea96e3da3056f39c2a5c78a25ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708973"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Benutzerdefinierte Dokumenteigenschaften in einem älteren Sprachdienst
Dokumenteigenschaften können im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaftenfenster** angezeigt werden. Programmiersprachen verfügen im Allgemeinen nicht über Eigenschaften, die einzelnen Quelldateien zugeordnet sind. XML unterstützt jedoch Dokumenteigenschaften, die sich auf die Codierung, das Schema und das Stylesheet auswirken.

## <a name="discussion"></a>Diskussion
 Wenn Ihre Sprache benutzerdefinierte Dokumenteigenschaften benötigt, müssen <xref:Microsoft.VisualStudio.Package.DocumentProperties> Sie eine Klasse aus der Klasse ableiten und die erforderlichen Eigenschaften für die abgeleitete Klasse implementieren.

 Darüber hinaus werden Dokumenteigenschaften in der Regel in der Quelldatei selbst gespeichert. Dies erfordert, dass der Sprachdienst die Eigenschafteninformationen aus der Quelldatei analysiert, die im **Eigenschaftenfenster** angezeigt werden, und die Quelldatei aktualisiert, wenn eine Änderung an den Dokumenteigenschaften im **Eigenschaftenfenster** vorgenommen wird.

## <a name="customize-the-documentproperties-class"></a>Anpassen der DocumentProperties-Klasse
 Um benutzerdefinierte Dokumenteigenschaften zu unterstützen, müssen <xref:Microsoft.VisualStudio.Package.DocumentProperties> Sie eine Klasse von der Klasse ableiten und so viele Eigenschaften hinzufügen, wie Sie benötigen. Sie sollten auch Benutzerattribute angeben, um sie in der **Eigenschaftenfensteranzeige** zu organisieren. Wenn eine Eigenschaft `get` nur über einen Accessor verfügt, wird sie im **Eigenschaftenfenster** schreibgeschützt angezeigt. Wenn eine Eigenschaft `get` `set` über beide und Accessoren verfügt, kann die Eigenschaft auch im **Eigenschaftenfenster** aktualisiert werden.

### <a name="example"></a>Beispiel
 Hier ist eine Beispielklasse, die von <xref:Microsoft.VisualStudio.Package.DocumentProperties>abgeleitet ist, die zwei Eigenschaften `Filename` und `Description`zeigt. Wenn eine Eigenschaft aktualisiert wird, <xref:Microsoft.VisualStudio.Package.LanguageService> wird eine benutzerdefinierte Methode für die Klasse aufgerufen, um die Eigenschaft in die Quelldatei zu schreiben.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>Instanziieren der benutzerdefinierten DocumentProperties-Klasse
 Um die benutzerdefinierten Dokumenteigenschaftenklassen zu instanziieren, müssen Sie <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> die Methode in der <xref:Microsoft.VisualStudio.Package.DocumentProperties> Version der Klasse überschreiben, um eine einzelne Instanz Ihrer Klasse zurückzugeben.

### <a name="example"></a>Beispiel

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>Eigenschaften in der Quelldatei
 Da Dokumenteigenschaften in der Regel spezifisch für die Quelldatei sind, werden die Werte in der Quelldatei selbst gespeichert. Dies erfordert Unterstützung durch den Sprachparser oder Scanner, um diese Eigenschaften zu definieren. Beispielsweise werden die Eigenschaften eines XML-Dokuments auf dem Stammknoten gespeichert. Die Werte auf dem Stammknoten werden geändert, wenn die **Eigenschaftenfensterwerte** geändert und der Stammknoten im Editor aktualisiert wird.

### <a name="example"></a>Beispiel
 In diesem Beispiel `Filename` `Description` werden die Eigenschaften und in den ersten beiden Zeilen der Quelldatei, eingebettet in einen speziellen Kommentarheader, wie:

```
//!Filename = file.testext
//!Description = A sample file
```

 Dieses Beispiel zeigt die beiden Methoden, die zum Abrufen und Festlegen der Dokumenteigenschaften aus den ersten beiden Zeilen der Quelldatei erforderlich sind, sowie, wie die Eigenschaften aktualisiert werden, wenn der Benutzer die Quelldatei direkt ändert. Die `SetPropertyValue` Methode im hier gezeigten Beispiel ist `TestDocumentProperties` dieselbe, die aus der Klasse aufgerufen wird, wie im *Customizing des DocumentProperties-Klassenabschnitts* gezeigt.

 In diesem Beispiel wird der Scanner verwendet, um den Tokentyp in den ersten beiden Zeilen zu bestimmen. Dieses Beispiel dient nur zur Veranschaulichung. Ein typischerer Ansatz für diese Situation besteht darin, die Quelldatei in eine so genannte Analysestruktur zu analysieren, in der jeder Knoten der Struktur Informationen zu einem bestimmten Token enthält. Der Stammknoten würde die Dokumenteigenschaften enthalten.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Legacy-Sprachdienstfunktionen](../../extensibility/internals/legacy-language-service-features1.md)
