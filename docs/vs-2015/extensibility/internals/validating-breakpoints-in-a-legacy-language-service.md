---
title: Überprüfen von Haltepunkten in einem Legacysprachdienst | Microsoft-Dokumentation
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
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2739bfd8807552653e7bb302e5e5efad2835529b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216839"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Überprüfen von Haltepunkten in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Haltepunkt gibt an, dass die Ausführung des Programms zu einem bestimmten Zeitpunkt beendet werden soll, während er in einem Debugger ausgeführt wird. Ein Benutzer kann einen Haltepunkt auf eine beliebige Zeile in der Quelldatei platziert werden, da der Editor keine Kenntnis hat der Frage, was auf einen gültigen Speicherort für einen Haltepunkt darstellt. Wenn der Debugger gestartet wird, werden alle markierten Haltepunkte (ausstehenden Haltepunkte genannt) an die entsprechende Position in das aktive Programm gebunden. Markieren Sie zur gleichen Zeit, die die Haltepunkte überprüft werden, um sicherzustellen, dass sie gültige Codepositionen aus. Ein Haltepunkt in einem Kommentar ist z. B. nicht gültig, da kein Code vorhanden, an dieser Stelle im Quellcode ist. Der Debugger deaktiviert ungültige Haltepunkte an.  
  
 Da der Sprachdienst über den Quellcode Anzeige weiß, können sie Haltepunkte überprüfen, bevor der Debugger gestartet wird. Sie können außer Kraft setzen der <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode, um eine Spanne angeben einen gültigen Speicherort für einen Haltepunkt zurückzugeben. Die Position des Haltepunkts wird weiterhin überprüft, wenn der Debugger wird gestartet, aber der Benutzer eine ungültige Haltepunkte Benachrichtigung ohne Wartezeiten für den Debugger geladen.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementieren der Unterstützung für das Überprüfen von Haltepunkten  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode erhält die Position des Haltepunkts. Ihre Implementierung muss entscheiden, ob der Speicherort gültig ist, und angeben, dass dies durch Rückgabe eines Textabschnitts, das der Code identifiziert, den Haltepunkt die Position der Zeile zugeordnet.  
  
-   Zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> ist der Speicherort gültig ist, oder <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> , wenn er nicht gültig ist.  
  
-   Wenn der Breakpoint gültig ist. wird der Textabschnitt zusammen mit dem Haltepunkt hervorgehoben.  
  
-   Wenn der Haltepunkt ungültig ist, wird eine Fehlermeldung in der Statusleiste angezeigt.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode, die den Parser, um den auszublendenden Codeabschnitt zu erhalten (sofern vorhanden) an der angegebenen Position aufruft.  
  
 In diesem Beispiel wird davon ausgegangen, dass Sie hinzugefügt haben, eine `GetCodeSpan` Methode, um die <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Klasse, die den Textabschnitt und gibt überprüft `true` , wenn es sich um einen gültigen Breakpoint-Speicherort ist.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)

