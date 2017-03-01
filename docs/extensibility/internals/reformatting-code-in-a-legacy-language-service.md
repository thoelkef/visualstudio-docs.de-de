---
title: Formatieren von Code in einer Legacy-Sprachdienst | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 12
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
translationtype: Machine Translation
ms.sourcegitcommit: 08d537f003279283509913d5f3d6aaa1bb1c4600
ms.openlocfilehash: d78fb976b3500a657d080634c6a041c218c3f1a1
ms.lasthandoff: 02/22/2017

---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Formatieren von Code in einer Legacy-Sprachdienst

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcode kann neu formatiert werden, werden zuerst die Verwendung der Einzüge und Leerzeichen. Dazu kann gehören, einfügen oder Entfernen von Leerzeichen oder Tabstopps am Anfang jeder Zeile, Hinzufügen neuer Zeilen zwischen den Zeilen oder Leerzeichen durch Tabstopps oder Leerzeichen Tabstopps ersetzen.  
  
>**Hinweis:** einfügen oder Löschen von Zeilenumbruchzeichen beeinträchtigt Marker, z. B. Haltepunkte und Lesezeichen, hinzufügen oder Entfernen von Leerzeichen oder Tabstopps wird jedoch nicht beeinträchtigt Marker.  
  
Benutzer können einen umformatieren Vorgang starten, indem Sie die Auswahl **Formatauswahl** oder **Dokument formatieren** aus der **erweitert** Menü auf die **bearbeiten** Menü. Ein umformatieren Vorgang kann auch ausgelöst werden, wenn ein Codeausschnitt oder ein bestimmtes Zeichen eingefügt wird. Z. B. Wenn Sie in c# eine schließende geschweifte Klammer eingeben, wird alles zwischen der geöffneten geschweiften Klammer und der schließenden geschweiften Klammer automatisch auf die richtige Ebene eingezogen.
  
Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sendet die **Formatauswahl** oder **Dokument formatieren** -Befehl an der Sprachdienst die <xref:Microsoft.VisualStudio.Package.ViewFilter>-Klasse ruft die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>Methode in der <xref:Microsoft.VisualStudio.Package.Source>Klasse.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter> Zur Unterstützung von Formatierung müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>-Methode und übergeben Sie eine eigene Formatierung code.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  
  
## <a name="enabling-support-for-reformatting"></a>Aktivieren der Unterstützung für formatieren  

Formatierung, unterstützen die `EnableFormatSelection` Parameter von der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>muss festgelegt werden, um `true` beim Registrieren Ihrer VSPackages.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Dadurch wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>-Eigenschaft `true`.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> Die <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>-Methode gibt den Wert dieser Eigenschaft.</xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Wenn sie der <xref:Microsoft.VisualStudio.Package.ViewFilter>Klasse aufruft, die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter> true zurückgibt  
  
## <a name="implementing-reformatting"></a>Neuformatieren implementieren

Um dabei zu implementieren, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source>Klasse, und überschreiben die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>-Methode.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.Source> Das <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Objekt beschreibt, das Span-Tag-Format und das <xref:Microsoft.VisualStudio.Package.EditArray>Objekt enthält, auf die span. vorgenommenen Bearbeitungen</xref:Microsoft.VisualStudio.Package.EditArray> </xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Beachten Sie, dass diese Spanne das gesamte Dokument sein kann. Da es sich wahrscheinlich mehrere Änderungen an die Spanne, sollten alle Änderungen jedoch in einer einzigen Aktion rückgängig gemacht sein. Umschließen Sie hierzu alle Änderungen in einem <xref:Microsoft.VisualStudio.Package.CompoundAction>-Objekt (in diesem Thema im Abschnitt "Verwenden der CompoundAction-Klasse").</xref:Microsoft.VisualStudio.Package.CompoundAction>

### <a name="example"></a>Beispiel  

Im folgende Beispiel sicherstellt, dass es ein Leerzeichen nach jedem Komma in der Auswahl, wenn das Komma von einer Registerkarte gefolgt wird oder am Ende der Zeile. Leerzeichen nach das letzte Komma in einer Zeile werden gelöscht. Finden Sie im Abschnitt "Verwenden der CompoundAction-Klasse" in diesem Thema finden Sie unter wie diese Methode aufgerufen wird, von der <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>-Methode.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>Mithilfe der CompoundAction-Klasse  
 
Alle der Neuformatieren auf einen Abschnitt eines Codes ausgeführt, sollte in einer einzigen Aktion rückgängig gemacht. Dies kann erreicht werden mithilfe einer <xref:Microsoft.VisualStudio.Package.CompoundAction>Klasse.</xref:Microsoft.VisualStudio.Package.CompoundAction> Diese Klasse umschließt eine Reihe von Bearbeitungsvorgänge im Text-Puffer in einer einzelnen Bearbeitungsvorgang.  
  
### <a name="example"></a>Beispiel

Es folgt ein Beispiel zur Verwendung der <xref:Microsoft.VisualStudio.Package.CompoundAction>Klasse.</xref:Microsoft.VisualStudio.Package.CompoundAction> Siehe das Beispiel im Abschnitt "Implementieren von Unterstützung für die Formatierung" in diesem Thema ein Beispiel für die `DoFormatting` Methode.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>Siehe auch

[Legacy-Dienst-Sprachfunktionen](legacy-language-service-features1.md)
