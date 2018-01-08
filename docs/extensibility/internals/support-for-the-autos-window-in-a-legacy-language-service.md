---
title: "Unterstützung für das Fenster \"Auto\" in einen Legacy-Sprachdienst | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: db6be625c671a508be3c2fd2f1697282af282bdd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Unterstützung für das Fenster "Auto" in einen Legacy-Sprachdienst
Die **"Auto"** Fenster zeigt Ausdrücke wie z. B. Variablen und Parametern, die im Bereich befinden, wenn das Programm, das gerade gedebuggt wird (entweder aufgrund von einem Haltepunkt oder einer Ausnahme) angehalten wird. Lokale oder globale, Variablen und Parametern, die im lokalen Bereich geändert wurden, können die Ausdrücke enthalten. Die **"Auto"** Fenster kann auch Instanziierungen von einer Klasse, Struktur oder einem anderen Typ enthalten. Elemente, die eine ausdrucksauswertung auswerten kann potenziell angezeigt werden kann die **"Auto"** Fenster.  
  
 Des managed Package Framework (MPF) bietet keine direkte Unterstützung für die **"Auto"** Fenster. Jedoch wenn Sie außer Kraft setzen die <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> -Methode, können Sie eine Liste von Ausdrücken in angezeigt werden Zurückgeben der **"Auto"** Fenster.  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementieren der Unterstützung für das Fenster "Auto"  
 Sie müssen lediglich zur Unterstützung der **"Auto"** Fenster wird zum Implementieren der <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Ihre Implementierung muss entscheiden, erhält eine Position in der Quelldatei, die Ausdrücke in angezeigt werden, sollten die **"Auto"** Fenster. Die Methode gibt eine Liste von Zeichenfolgen, die in denen jede Zeichenfolge einen einzelnen Ausdruck darstellt. Ein Rückgabewert von <xref:Microsoft.VisualStudio.VSConstants.S_OK> gibt an, dass die Liste mit Ausdrücken enthält während <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> gibt an, dass es keine Ausdrücke sind angezeigt.  
  
 Die tatsächliche zurückgegebene Ausdrücke sind die Namen der Variablen oder Parameter, die an dieser Stelle im Code angezeigt werden. Diese Namen werden an der ausdrucksauswertung zum Abrufen von Werten und Typen, die in angezeigt werden übergeben der **"Auto"** Fenster.  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Implementierung von der <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> -Methode, die eine Liste von Ausdrücken aus Ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode, die den Grund für die Analyse mit <xref:Microsoft.VisualStudio.Package.ParseReason>. Jede der Ausdrücke als umschlossen ist ein `TestVsEnumBSTR` , implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> Schnittstelle.  
  
 Beachten Sie, dass die `GetAutoExpressionsCount` und `GetAutoExpression` sind benutzerdefinierte Methoden auf die `TestAuthoringSink` Objekt und zur Unterstützung dieses Beispiel hinzugefügt wurden. Sie repräsentieren eine Möglichkeit, in welche Ausdrücken hinzugefügt der `TestAuthoringSink` Objekt vom Parser (durch Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> Methode) außerhalb der Parser zugegriffen werden kann.  
  
```csharp  
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