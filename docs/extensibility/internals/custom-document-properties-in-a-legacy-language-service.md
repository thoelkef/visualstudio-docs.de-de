---
title: Benutzerdefinierte Dokumenteigenschaften in einen Legacy-Sprachdienst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc4706a7cd1a666da8562ce78de5af9366c69fab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Benutzerdefinierte Dokumenteigenschaften in einen Legacy-Sprachdienst
Dokumenteigenschaften angezeigt werden können, der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaften** Fenster. Programmiersprachen müssen im Allgemeinen nicht einzelne Quelldateien zugeordnete Eigenschaften. Allerdings unterstützt XML Dokumenteigenschaften, die Auswirkungen auf die Codierung, Schema und Stylesheet.  
  
## <a name="discussion"></a>Diskussion  
 Wenn Ihre Sprache benutzerdefinierte Dokumenteigenschaften benötigt werden, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.DocumentProperties> Klasse und implementieren Sie die erforderlichen Eigenschaften für die abgeleitete Klasse.  
  
 Darüber hinaus werden die Dokumenteigenschaften in der Regel in der Quelldatei selbst gespeichert. Dies erfordert, dass der Sprachdienst beim Analysieren von Informationen über die Eigenschaft aus der Quelldatei für die anzuzeigenden in der **Eigenschaften** Fenster und die Quelldatei zu aktualisieren, wenn eine Änderung, um die Dokumenteigenschaften in vorgenommen wird der  **Eigenschaften** Fenster.  
  
## <a name="customizing-the-documentproperties-class"></a>Anpassen der DocumentProperties-Klasse  
 Unterstützung von benutzerdefinierten Dokumenteigenschaften, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.DocumentProperties> -Klasse und fügen Sie beliebig viele Eigenschaften. Sie müssen auch angeben, Benutzerattribute zum Organisieren von in der **Eigenschaften** angezeigt. Wenn eine Eigenschaft verfügt nur über eine `get` Accessor wird veranschaulicht, wie in schreibgeschützt der **Eigenschaften** Fenster. Wenn eine Eigenschaft, die beides aufweist `get` und `set` Accessoren die Eigenschaft auch aktualisiert werden der **Eigenschaften** Fenster.  
  
### <a name="example"></a>Beispiel  
 Hier ist eine Beispielklasse, die von abgeleiteten <xref:Microsoft.VisualStudio.Package.DocumentProperties>, dabei werden zwei Eigenschaften, Dateiname und die Beschreibung angezeigt. Wenn eine Eigenschaft aktualisiert wird, eine benutzerdefinierte Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse aufgerufen, um die Eigenschaft in der Quelldatei schreiben.  
  
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
  
## <a name="instantiating-the-custom-documentproperties-class"></a>Instanziieren die benutzerdefinierte DocumentProperties-Klasse  
 Um die benutzerdefinierten Eigenschaften Dokumentklasse zu instanziieren, müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> Methode in Ihrer Version von den <xref:Microsoft.VisualStudio.Package.LanguageService> zurückzugebenden eine einzelne Instanz der Klasse Ihre <xref:Microsoft.VisualStudio.Package.DocumentProperties> Klasse.  
  
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
 Da Dokumenteigenschaften in der Regel für die Quelldatei spezifisch sind, werden die Werte in der Quelldatei selbst gespeichert. Dies erfordert die Unterstützung von der Sprachenparser oder Scanner mit diesen Eigenschaften definieren. Beispielsweise werden die Eigenschaften eines XML-Dokuments für den Stammknoten gespeichert. Die Werte für den Stammknoten werden geändert, wenn die **Eigenschaften** Fenster Werte geändert werden, und der Stammknoten wird im Editor aktualisiert.  
  
### <a name="example"></a>Beispiel  
 In diesem Beispiel werden die Eigenschaften "Filename" und "Description" in den ersten beiden Zeilen der Quelldatei, in einem Header spezielle Kommentar als eingebettet gespeichert:  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 Dieses Beispiel zeigt die beiden Methoden zum Abrufen und Festlegen von Dokumenteigenschaften aus den ersten beiden Zeilen der Quelldatei als auch, wie die Eigenschaften aktualisiert werden, wenn der Benutzer direkt die Quelldatei ändert. Die `SetPropertyValue` im entspricht dem hier gezeigten Beispiel eines Methodenaufrufs aus der `TestDocumentProperties` -Klasse wie im Abschnitt "Anpassen der DocumentProperties-Klasse" dargestellt.  
  
 In diesem Beispiel verwendet der Scanner auf um den Typ von Token in den ersten beiden Zeilen zu bestimmen. In diesem Beispiel wird nur zur Veranschaulichung. Ein üblicher Ansatz für dieses Problem ist, die Quelldatei in was eine Analysestruktur aufgerufen wird, in dem Informationen über ein bestimmtes Token enthält jeder Knoten der Struktur zu analysieren. Der Stammknoten würde die Dokumenteigenschaften enthalten.  
  
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
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)