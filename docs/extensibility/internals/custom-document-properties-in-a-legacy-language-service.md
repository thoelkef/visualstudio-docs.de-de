---
title: Benutzerdefinierte Dokumenteigenschaften in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98402a61629b48b25a8636aaf6a912e89c283951
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605834"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Benutzerdefinierte Dokumenteigenschaften in einem legacysprachdiensten
Dokumenteigenschaften können angezeigt werden, der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaften** Fenster. Programmiersprachen haben in der Regel keine einzelnen Dateien zugeordnete Eigenschaften. Allerdings unterstützt XML-Dokumenteigenschaften, die die Codierung, Schema und Stylesheet betreffen.

## <a name="discussion"></a>Diskussion
 Wenn Ihre Sprache benutzerdefinierte Dokumenteigenschaften benötigt, müssen Sie leiten eine Klasse von der <xref:Microsoft.VisualStudio.Package.DocumentProperties> Klasse und implementieren Sie die erforderlichen Eigenschaften für die abgeleitete Klasse.

 Darüber hinaus werden die Dokumenteigenschaften in der Regel in der Quelldatei selbst gespeichert. Dies erfordert, dass den Sprachdienst, zum Analysieren von Informationen über die Eigenschaft aus der Quelldatei anzuzeigenden der **Eigenschaften** Fenster und die Quelldatei zu aktualisieren, wenn eine Änderung, um die Dokumenteigenschaften in vorgenommen wird die  **Eigenschaften** Fenster.

## <a name="customize-the-documentproperties-class"></a>Anpassen der DocumentProperties-Klasse
 Zur Unterstützung von benutzerdefinierten Dokumenteigenschaften, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.DocumentProperties> -Klasse und das Hinzufügen beliebig viele Eigenschaften, die Sie benötigen. Sie sollten auch angeben, Benutzerattribute, die zum Organisieren von in die **Eigenschaften** Fenster angezeigt. Wenn eine Eigenschaft verfügt nur über eine `get` Accessor wird angezeigt, als schreibgeschützt in der **Eigenschaften** Fenster. Wenn eine Eigenschaft, die beides aufweist `get` und `set` -Accessor angeben, die Eigenschaft auch aktualisiert werden der **Eigenschaften** Fenster.

### <a name="example"></a>Beispiel
 Hier ist eine Beispielklasse, die von abgeleiteten <xref:Microsoft.VisualStudio.Package.DocumentProperties>, mit zwei Eigenschaften, `Filename` und `Description`. Wenn eine Eigenschaft aktualisiert wird, eine benutzerdefinierte Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse wird aufgerufen, um die Eigenschaft in der Quelldatei zu schreiben.

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

## <a name="instantiate-the-custom-documentproperties-class"></a>Instanziieren Sie die benutzerdefinierte DocumentProperties-Klasse
 Um die benutzerdefinierten Eigenschaften Dokumentklasse zu instanziieren, müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> -Methode in Ihrer Version von der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse die Rückgabe einer einzelnen Instanz von Ihr <xref:Microsoft.VisualStudio.Package.DocumentProperties> Klasse.

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
 Da die Dokumenteigenschaften für die Quelldatei in der Regel spezifisch sind, werden die Werte in der Quelldatei selbst gespeichert. Dies erfordert die Unterstützung durch die Sprachenparser oder den Scanner, um diese Eigenschaften zu definieren. Beispielsweise werden die Eigenschaften eines XML-Dokuments für den Stammknoten gespeichert. Die Werte für den Stammknoten werden geändert, wenn die **Eigenschaften** Werte geändert werden, und der Stammknoten wird im Editor aktualisiert.

### <a name="example"></a>Beispiel
 In diesem Beispiel speichert die Eigenschaften `Filename` und `Description` in den ersten beiden Zeilen der Quelldatei, in einem besonderen Kommentar-Header als eingebettet:

```
//!Filename = file.testext
//!Description = A sample file
```

 Dieses Beispiel zeigt die beiden Methoden zum Abrufen und die Dokumenteigenschaften aus der Quelldatei sowie die ersten beiden Zeilen festlegen, wie die Eigenschaften aktualisiert werden, wenn der Benutzer die Quelldatei direkt bearbeitet werden. Die `SetPropertyValue` -Methode in dem Beispiel, das hier ist identisch, die eine aus aufgerufen der `TestDocumentProperties` -Klasse wie im dargestellt die *Anpassen der Klasse DocumentProperties* Abschnitt.

 Dieses Beispiel verwendet die Überprüfung, um den Typ des Tokens in den ersten beiden Zeilen zu bestimmen. In diesem Beispiel ist nur zur Veranschaulichung. Ein üblicher Ansatz für dieses Problem ist beim Analysieren der Quelldatei in die eine Analysestruktur bezeichnet wird, von denen jeder Knoten der Struktur Informationen über ein bestimmtes Token enthält. Der Stammknoten enthält die Dokumenteigenschaften.

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

## <a name="see-also"></a>Siehe auch
- [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)