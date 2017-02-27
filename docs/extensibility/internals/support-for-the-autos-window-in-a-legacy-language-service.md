---
title: "Unterst&#252;tzung f&#252;r das Fenster &quot;Auto&quot; in eine Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sprachdienste [Verwaltetes Paketframework], Fenster "Auto""
  - "Fenster "Auto", Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Unterst&#252;tzung f&#252;r das Fenster &quot;Auto&quot; in eine Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Fenster wird **Auto** Ausdrücke wie Variablen und Parameter an, die im Bereich enthalten sind, wenn das Programm, das gedebuggt wird, unterbrochen wird \(entweder aufgrund eines Haltepunkts oder einer Ausnahme\).  Die Ausdrücke können Variablen, lokal oder global und Parameter enthalten, die im lokalen Gültigkeitsbereich geändert wurden.  Das **Auto** Fenster kann Instanziierungen einer Klasse, Struktur oder einer anderen ebenfalls einbeziehen Typ.  Alles, was ein Ausdrucksauswertung ausgewertet werden kann, kann im Fenster **Auto** möglicherweise angezeigt werden.  
  
 Das verwaltete Paketframework \(MPF\) bietet keine direkte Unterstützung für das **Auto** Fenster.  Wenn Sie jedoch die <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>\-Methode überschreiben, können Sie eine Liste der im Fenster **Auto** darzustellenden Ausdruck zurückgegeben wird.  
  
## Unterstützung für das Implementieren Automobil\-Fenster  
 Alles, was Sie tun müssen, um das Fenster zu unterstützen **Auto** darin, die <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse zu implementieren.  Die Implementierung muss entscheiden, wenn eine Position in der Quelldatei, die Ausdrücke im **Auto** Fenster aussehen sollten.  Die Methode gibt eine Liste von Zeichenfolgen zurück, wobei jede Zeichenfolge einen einzelnen Ausdruck darstellt.  Der Rückgabewert <xref:Microsoft.VisualStudio.VSConstants.S_OK> gibt an, dass die Liste Ausdrücke enthält, während <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> angibt, dass keine Ausdrücke dargestellt wird.  
  
 Die tatsächlich zurückgegebenen Ausdrücke sind die Namen der Variablen oder Parameter, die an dieser Stelle im Code angezeigt werden.  Diese Namen werden zum Übergeben der Ausdrucksauswertung zum Abrufen von Werten und Typen, die dann im **Auto** Fenster angezeigt werden.  
  
### Beispiel  
 Im folgenden Beispiel wird eine Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>\-Methode auf, die eine Liste von Ausdrücken aus der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>\-Methode mit dem grunds Analyse <xref:Microsoft.VisualStudio.Package.ParseReason>abruft.  Alle Ausdrücke werden als `TestVsEnumBSTR` umschlossen, der die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>\-Schnittstelle implementiert.  
  
 Beachten Sie, dass die `GetAutoExpressionsCount` und Methoden `GetAutoExpression` benutzerdefinierte Methoden im `TestAuthoringSink`\-Objekt entsprechen und hinzugefügt wurden, um dieses Beispiel zu unterstützen.  Sie stellen eine Möglichkeit dar, in der die Ausdrücke, die dem `TestAuthoringSink`\-Objekt vom Parser \(durch Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>\-Methode\) hinzugefügt werden außerhalb des Parsers zugegriffen werden kann.  
  
```c#  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```