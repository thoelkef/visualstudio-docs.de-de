---
title: "Benutzerdefinierte Dokumenteigenschaften in einer Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "benutzerdefinierte Dokumenteigenschaften Sprachdienste [Verwaltetes Paketframework]"
  - "benutzerdefinierte Dokumenteigenschaften"
  - "Sprachdienste [Verwaltetes Paketframework], benutzerdefinierte Dokumenteigenschaften"
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Benutzerdefinierte Dokumenteigenschaften in einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dokumenteigenschaften können im Fenster [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaften** angezeigt werden.  Programmiersprachen im Allgemeinen verfügen nicht über die Eigenschaften, die mit den einzelnen Quelldateien zugeordnet sind. Allerdings unterstützt XML Dokumenteigenschaften, die die Codierung, das Schema und das Stylesheet auswirken.  
  
## Erörterung  
 Wenn die Sprache benutzerdefinierte Dokumenteigenschaften erfordert, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.DocumentProperties>\-Klasse ableiten und die erforderlichen Eigenschaften für die abgeleiteten Klasse implementieren.  
  
 Darüber hinaus werden Dokumenteigenschaften in der Regel in der Quelldatei selbst gespeichert.  Dies erfordert den Sprachdienst, die Eigenschaft aus der Quelldatei zu analysieren, um **Eigenschaften** im Fenster anzeigen und die Quelldatei zu aktualisieren, wenn eine Änderung an den Dokumenteigenschaften in **Eigenschaften** Fenster vorgenommen wird.  
  
## Die DocumentProperties\-Klasse anpassen  
 Um benutzerdefinierte Dokumenteigenschaften zu unterstützen, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.DocumentProperties>\-Klasse ableiten und so viele Eigenschaften hinzufügen Sie benötigen.  Sie können auch Attribute für Benutzer bereitstellen, das in der **Eigenschaften** Fenster Anzeige zu organisieren.  Wenn eine Eigenschaft nur einen `get` Accessor verfügt, wird diese als schreibgeschützt angezeigt **Eigenschaften** im Fenster.  Wenn eine Eigenschaft `get` und `set` kann Accessoren der Eigenschaft im Fenster **Eigenschaften** ebenfalls aktualisiert werden.  
  
### Beispiel  
 Im Folgenden finden Sie eine Beispielklasse, die von <xref:Microsoft.VisualStudio.Package.DocumentProperties>abgeleitet wird, und es werden zwei Eigenschaften, Dateinamen und Beschreibung angezeigt.  Wenn eine Eigenschaft aktualisiert wird, wird eine benutzerdefinierte Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klassen aufgerufen, um die Eigenschaft zur Quelldatei zu schreiben.  
  
```c#  
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
  
## Die benutzerdefinierte DocumentProperties\-Klasse instanziieren  
 Um die benutzerdefinierte Dokumenteigenschaften Klasse zu instanziieren, müssen Sie die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>\-Methode in der Version der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse überschreiben um eine einzelne Instanz der <xref:Microsoft.VisualStudio.Package.DocumentProperties>\-Klasse zurückgegeben wird.  
  
### Beispiel  
  
```c#  
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
  
## Eigenschaften in der Quelldatei  
 Da Dokumenteigenschaften in der Regel zur Quelldatei beziehen, werden die Werte in der Quelldatei selbst gespeichert.  Dies erfordert Unterstützung von Sprachen, Scanner oder der Parser diese Eigenschaften zu definieren.  Beispielsweise werden die Eigenschaften eines XML\-Dokuments im Stammknoten gespeichert.  Die Werte für den Stammknoten wird geändert, wenn die Attributwerte **Eigenschaften** Fenster geändert werden, und der Knoten wird im Editor aktualisiert.  
  
### Beispiel  
 In diesem Beispiel werden die Eigenschaften „Dateiname“ und „Beschreibung“ in den ersten beiden Zeilen der Quelldatei, eingebettet in einem speziellen Header Kommentar, z. B.:  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 In diesem Beispiel werden die beiden Möglichkeiten gezeigt, die erforderlich sind, um die Dokumenteigenschaften in den ersten beiden Zeilen der Quelldatei sowie zum Abrufen und Festlegen der Eigenschaften aktualisiert werden, wenn der Benutzer die Quelldatei direkt geändert wird.  Die `SetPropertyValue`\-Methode im Beispiel, das hier angezeigt wird, ist die gleiche Klasse `TestDocumentProperties` aus der Aufruf wie im Abschnitt „Anpassen der DocumentProperties\-Klasse“ dargestellt.  
  
 In diesem Beispiel wird der Scanner, um den Typ des Tokens in den ersten beiden Zeilen zu bestimmen.  Dieses Beispiel ist nur zur Veranschaulichung.  Ein typischerer Ansatz zu dieser Situation ist, zu analysieren, was die Quelldatei in eine Analysestruktur aufgerufen wird, wobei jeder Knoten der Struktur Informationen über ein bestimmtes Token enthält.  Der Stammknoten würde die Dokumenteigenschaften enthalten.  
  
```c#  
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
  
## Siehe auch  
 [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)