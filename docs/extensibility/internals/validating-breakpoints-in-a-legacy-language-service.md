---
title: "Überprüfen die Haltepunkte in einem Legacy-Sprachdienst | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2a87c22948e710a3b95ee7f79b31626794dc7708
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Überprüfen die Haltepunkte in einem Legacy-Sprachdienst
Ein Haltepunkt gibt an, dass die Ausführung des Programms zu einem bestimmten Zeitpunkt beendet werden soll, während er in einem Debugger ausgeführt wird. Benutzer kann einen Haltepunkt für jede beliebige Zeile in der Quelldatei platziert werden, da der Editor keine Kenntnis hat von was einen gültigen Speicherort für einen Breakpoint ausmacht. Wenn der Debugger gestartet wird, werden alle markierten Haltepunkte (ausstehenden Haltepunkte genannt) an die gewünschte Position in der ausgeführten Anwendung gebunden. Markieren Sie zum gleichen Zeitpunkt Breakpoints überprüft werden, um sicherzustellen, dass sie gültige Codepositionen aus. Beispielsweise ist ein Breakpoint für einen Kommentar ungültig, da es an dieser Stelle im Quellcode kein Code ist. Der Debugger deaktiviert ungültige Haltepunkte.  
  
 Da der Quellcode mehr angezeigt wird der Sprachdienst kennt, können sie Haltepunkte überprüfen, bevor der Debugger gestartet wird. Sie können außer Kraft setzen die <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode, um eine Spanne angeben einen gültigen Speicherort für einen Breakpoint zurückzugeben. Die Position des Haltepunkts ist immer noch überprüft werden, wenn der Debugger wird gestartet, aber der Benutzer eine ungültige Haltepunkte Benachrichtigung ohne zu warten, damit des Debuggers geladen werden.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementieren der Unterstützung für die Überprüfung von Haltepunkten  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> -Methode erhält die Position des Haltepunkts. Ihre Implementierung muss entscheiden, unabhängig davon, ob der Speicherort gültig ist, und darauf hinweisen, dass dies wird durch Zurückgeben von einem Textabschnitt, der den Code identifiziert den Breakpoint die Position der Zeile zugeordnet.  
  
-   Zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> Wenn der Speicherort gültig ist oder <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> , wenn er ungültig ist.  
  
-   Wenn der Breakpoint gültig ist wird zusammen mit den Haltepunkt des Textabschnitts hervorgehoben.  
  
-   Wenn der Breakpoint ungültig ist, wird eine Fehlermeldung in der Statusleiste angezeigt.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Methode, die den Parser, um die Spanne des Codes zu erhalten (sofern vorhanden) am angegebenen Speicherort aufruft.  
  
 In diesem Beispiel wird davon ausgegangen, dass Sie hinzugefügt haben, eine `GetCodeSpan` Methode, um die <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Klasse, die dem Textabschnitt und gibt überprüft `true` Wenn es sich um einen gültigen Breakpoint Speicherort handelt.  
  
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
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)
