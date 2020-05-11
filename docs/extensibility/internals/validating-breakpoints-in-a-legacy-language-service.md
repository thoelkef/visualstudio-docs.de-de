---
title: Überprüfen von Haltepunkten in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704099"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Überprüfen von Haltepunkten in einem Legacysprachdienst
Ein Haltepunkt gibt an, dass die Programmausführung an einem bestimmten Punkt beendet werden soll, während sie in einem Debugger ausgeführt wird. Ein Benutzer kann einen Haltepunkt in einer beliebigen Zeile in der Quelldatei platzieren, da der Editor keine Kenntnis davon hat, was einen gültigen Speicherort für einen Haltepunkt darstellt. Wenn der Debugger gestartet wird, sind alle markierten Haltepunkte (als ausstehende Haltepunkte bezeichnet) an die entsprechende Position im laufenden Programm gebunden. Gleichzeitig werden die Haltepunkte überprüft, um sicherzustellen, dass sie gültige Codepositionen markieren. Beispielsweise ist ein Haltepunkt für einen Kommentar ungültig, da kein Code an dieser Stelle im Quellcode vorhanden ist. Der Debugger deaktiviert ungültige Haltepunkte.

 Da der Sprachdienst den angezeigten Quellcode kennt, kann er Haltepunkte überprüfen, bevor der Debugger gestartet wird. Sie können die <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode überschreiben, um eine Spanne zurückzugeben, die einen gültigen Speicherort für einen Haltepunkt angibt. Der Haltepunktspeicherort wird beim Starten des Debuggers noch überprüft, aber der Benutzer wird über ungültige Haltepunkte benachrichtigt, ohne auf das Laden des Debuggers zu warten.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementieren der Unterstützung für die Validierung von Haltepunkten

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode erhält die Position des Haltepunkts. Die Implementierung muss entscheiden, ob der Speicherort gültig ist, und dies angeben, indem Sie eine Textspanne zurückgeben, die den Code identifiziert, der der Zeilenposition des Haltepunkts zugeordnet ist.

- Gibt <xref:Microsoft.VisualStudio.VSConstants.S_OK> zurück, wenn der <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> Speicherort gültig oder ungültig ist.

- Wenn der Haltepunkt gültig ist, wird die Textspanne zusammen mit dem Haltepunkt hervorgehoben.

- Wenn der Haltepunkt ungültig ist, wird in der Statusleiste eine Fehlermeldung angezeigt.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Implementierung der Methode, die den Parser aufruft, um die Codespanne (falls vorhanden) an der angegebenen Position abzufragen.

 In diesem Beispiel wird `GetCodeSpan` davon ausgegangen, dass Sie der Klasse eine Methode hinzugefügt haben, die <xref:Microsoft.VisualStudio.Package.AuthoringSink> die Textspanne überprüft und zurückgibt, `true` wenn es sich um eine gültige Haltepunktposition handelt.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

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
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
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

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
