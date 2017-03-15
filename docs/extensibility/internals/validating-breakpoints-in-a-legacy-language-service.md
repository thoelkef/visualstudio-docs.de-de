---
title: "&#220;berpr&#252;fen die Haltepunkte in einem Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Haltepunkt-Überprüfung"
  - "Sprachdienste [Verwaltetes Paketframework], Haltepunkt-Überprüfung"
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# &#220;berpr&#252;fen die Haltepunkte in einem Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Haltepunkt gibt an, dass die Programmausführung an einem bestimmten Punkt beenden soll, sobald sie in einem Debugger ausgeführt wird.  Ein Benutzer kann einen Haltepunkt für jede Zeile in der Quelldatei platzieren, wie der Editor kein Wissen enthält, die einen gültigen Speicherort für einen Haltepunkt bildet.  Wenn der Debugger gestartet wird, werden alle ausgewählten Haltepunkte Haltepunkte ausstehende \(\) in den entsprechenden Stelle im laufenden Programm gebunden.  Gleichzeitig werden die Haltepunkte überprüft, um sicherzustellen, dass sie gültige Speicherorte Code kennzeichnen.  Beispielsweise ist ein Haltepunkt für einen Kommentar ungültig, da es keinen Code an dieser Stelle im Quellcode vorhanden sind.  Der Debugger deaktiviert ungültigen Haltepunkts.  
  
 Da der Sprachdienst im Quellcode auskennt, der angezeigt wird, kann er Haltepunkte überprüfen, bevor der Debugger gestartet wird.  Sie können die <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>\-Methode überschreiben, um eine Spanne zurückzugeben einen gültigen Speicherort für einen Haltepunkt angibt.  Die Haltepunktposition wird weiterhin überprüft, wenn der Debugger gestartet wird. Der Benutzer wird aus ungültigen Haltepunkts benachrichtigt, ohne darauf zu warten, dass der Debugger geladen werden soll.  
  
## Unterstützung für die Überprüfung von Haltepunkten implementieren  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>\-Methode entspricht der Position des Haltepunkts angegeben.  Die Implementierung muss entscheiden, ob der Speicherort angeben, das gültig ist, indem er einen Textabschnitt zurückgibt, der den Code bezeichnet, der mit der Zeilenposition der Haltepunkt zugeordnet ist.  
  
-   Geben Sie <xref:Microsoft.VisualStudio.VSConstants.S_OK> , wenn die Position gültig ist, oder <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> , wenn er nicht gültig ist.  
  
-   Wenn der Haltepunkt gültig ist, wird der Textabschnitt zusammen mit dem Haltepunkt markiert.  
  
-   Wenn der Haltepunkt nicht gültig ist, wird eine Fehlermeldung in der Statusleiste.  
  
### Beispiel  
 In diesem Beispiel wird eine Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>\-Methode auf, die den Parser aufgerufen wird, um die Spanne des Codes \(sofern vorhanden\) an der angegebenen Position abrufen.  
  
 In diesem Beispiel wird davon ausgegangen, dass Sie eine `GetCodeSpan`\-Methode zur <xref:Microsoft.VisualStudio.Package.AuthoringSink>\-Klasse hinzugefügt haben, die den Textabschnitt überprüft und `true` zurückgibt, wenn es sich um eine gültige Haltepunktposition wird.  
  
```c#  
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
  
## Siehe auch  
 [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)