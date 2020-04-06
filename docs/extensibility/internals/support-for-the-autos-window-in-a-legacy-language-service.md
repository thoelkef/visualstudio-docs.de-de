---
title: Unterstützung für das Autofenster in einem Legacy Language Service | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704885"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Unterstützen des Auto-Fensters in einem Legacysprachdienst
Das **Fenster Autos** zeigt Ausdrücke wie Variablen und Parameter an, die sich im Gültigkeitsbereich befinden, wenn das zu debuggende Programm angehalten wird (entweder aufgrund eines Haltepunkts oder einer Ausnahme). Die Ausdrücke können Variablen, lokale oder globale, und Parameter enthalten, die im lokalen Bereich geändert wurden. Das **Fenster "Autos"** kann auch Instanziierungen einer Klasse, Struktur oder eines anderen Typs enthalten. Alles, was ein Ausdrucksbewerter auswerten kann, kann möglicherweise im **Fenster "Autos"** angezeigt werden.

 Das Verwaltete Paketframework (Managed Package Framework, MPF) bietet keine direkte Unterstützung für das **Fenster Autos.** Wenn Sie die <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Methode jedoch überschreiben, können Sie eine Liste von Ausdrücken zurückgeben, die im Fenster **Autos** angezeigt werden sollen.

## <a name="implementing-support-for-the-autos-window"></a>Implementieren der Unterstützung für das Autofenster
 Alles, was Sie tun müssen, um <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> das Fenster <xref:Microsoft.VisualStudio.Package.LanguageService> **Autos** zu unterstützen, ist die Implementierung der Methode in der Klasse. Ihre Implementierung muss unter Angabe eines Speicherorts in der Quelldatei entscheiden, welche Ausdrücke im **Fenster Autos** angezeigt werden sollen. Die Methode gibt eine Liste von Zeichenfolgen zurück, in denen jede Zeichenfolge einen einzelnen Ausdruck darstellt. Ein Rückgabewert <xref:Microsoft.VisualStudio.VSConstants.S_OK> von gibt an, <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> dass die Liste Ausdrücke enthält, während angegeben wird, dass keine Ausdrücke angezeigt werden sollen.

 Die tatsächlich zurückgegebenen Ausdrücke sind die Namen der Variablen oder Parameter, die an dieser Position im Code angezeigt werden. Diese Namen werden an den Ausdrucksevaluator übergeben, um Werte und Typen zu erhalten, die dann im **Fenster Autos** angezeigt werden.

### <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> eine Implementierung der Methode, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> die eine Liste <xref:Microsoft.VisualStudio.Package.ParseReason>von Ausdrücken aus der Methode mithilfe des Analysegrunds abruft. Jeder der Ausdrücke wird `TestVsEnumBSTR` als ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> umschlossen, das die Schnittstelle implementiert.

 Beachten Sie, dass die `GetAutoExpressionsCount` und-Methoden `GetAutoExpression` benutzerdefinierte Methoden für das `TestAuthoringSink` Objekt sind und hinzugefügt wurden, um dieses Beispiel zu unterstützen. Sie stellen eine Möglichkeit dar, `TestAuthoringSink` auf die aus, auf <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> die aus, die dem Objekt vom Parser hinzugefügt werden (durch Aufrufen der Methode), außerhalb des Parsers zugegriffen werden kann.

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
