---
title: Unterstützung für das Fenster "Auto" in einem Legacysprachdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05a3181206f9e73ffe7800a581fc93c3712c4afa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283620"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Unterstützen des Auto-Fensters in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die **"Auto"** Fenster werden Ausdrücke wie z. B. Variablen und Parametern, die im Gültigkeitsbereich befinden, wenn die zu debuggende Programm wird (entweder aufgrund eines Haltepunkts oder einer Ausnahme) angehalten wird angezeigt. Die Ausdrücke können einschließen, lokalen oder globalen Variablen und Parametern, die im lokalen Bereich geändert wurden. Die **"Auto"** Fenster kann auch Instanziierungen von einer Klasse, Struktur oder einem anderen Typ enthalten. Alle Elemente, die eine ausdrucksauswertung auswerten kann potenziell angezeigt werden die **"Auto"** Fenster.  
  
 Das managed Package Framework (MPF) bietet keine direkte Unterstützung für die **"Auto"** Fenster. Jedoch wenn Sie außer Kraft setzen der <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> -Methode, Sie können eine Liste von Ausdrücken, die angezeigt werden sollen Zurückgeben der **"Auto"** Fenster.  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementieren der Unterstützung für das Fenster "Auto"  
 Sie müssen lediglich zur Unterstützung der **"Auto"** Fenster ist die Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Ihre Implementierung muss entscheiden, erhalten einen Speicherort in der Quelldatei, die Ausdrücke in angezeigt werden, sollten die **"Auto"** Fenster. Die-Methode gibt eine Liste von Zeichenfolgen, die in denen jede Zeichenfolge mit einen einzelnen Ausdruck darstellt. Der Rückgabewert <xref:Microsoft.VisualStudio.VSConstants.S_OK> gibt an, dass die Liste mit Ausdrücken enthält zwar <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> gibt an, dass es keine Ausdrücke sind angezeigt.  
  
 Die tatsächliche Ausdrücke, die zurückgegeben werden die Namen der Variablen oder Parameter, die an dieser Stelle im Code angezeigt werden. Diese Namen werden an der ausdrucksauswertung zum Abrufen der Werte und Typen, die Sie dann im angezeigten übergeben die **"Auto"** Fenster.  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> -Methode, die eine Liste der Ausdrücke aus der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode, die mithilfe des Grunds für die Analyse <xref:Microsoft.VisualStudio.Package.ParseReason>. Jeder Ausdruck wird als umschlossen eine `TestVsEnumBSTR` , implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> Schnittstelle.  
  
 Beachten Sie, dass die `GetAutoExpressionsCount` und `GetAutoExpression` sind benutzerdefinierte Methoden auf die `TestAuthoringSink` Objekt aus, und wurden hinzugefügt, um dieses Beispiel zu ermöglichen. Währungseinheiten auf verschiedene Weise in der Ausdrücke, die hinzugefügt, die `TestAuthoringSink` Objekt vom Parser (durch Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> Methode) außerhalb der Parser zugegriffen werden kann.  
  
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

