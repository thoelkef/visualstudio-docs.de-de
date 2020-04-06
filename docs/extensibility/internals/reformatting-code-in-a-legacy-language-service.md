---
title: Neuformatieren von Code in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705907"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Neuformatieren von Code in einem Legacysprachdienst

Im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcode kann durch Normalisierung der Verwendung von Einzügen und Leerzeichen neu formatiert werden. Dies kann das Einfügen oder Entfernen von Leerzeichen oder Registerkarten am Anfang jeder Zeile, das Hinzufügen neuer Linien zwischen Linien oder das Ersetzen von Leerzeichen durch Registerkarten oder Registerkarten durch Leerzeichen umfassen.

> [!NOTE]
> Das Einfügen oder Löschen von Zeilenumbruchzeichen kann sich auf Markierungen wie Haltepunkte und Lesezeichen auswirken, das Hinzufügen oder Entfernen von Leerzeichen oder Registerkarten wirkt sich jedoch nicht auf Marker aus.

Benutzer können einen Neuformatierungsvorgang starten, indem sie im Menü **Erweitert** im Menü **Bearbeiten** **Formatauswahl** oder **Dokument formatieren** auswählen. Ein Neuformatierungsvorgang kann auch ausgelöst werden, wenn ein Codeausschnitt oder ein bestimmtes Zeichen eingefügt wird. Wenn Sie z. B. eine schließende geschweifte Geschbungsebene in C- eingeben, wird alles zwischen der übereinstimmenden offenen geschweiften Klammer und der erforderlichen geschweiften Klammer automatisch auf die richtige Ebene eingerückt.

Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der Befehl **Formatauswahl** oder **Formatdokument** an <xref:Microsoft.VisualStudio.Package.ViewFilter> den <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> Sprachdienst <xref:Microsoft.VisualStudio.Package.Source> gesendet wird, ruft die Klasse die Methode in der Klasse auf. Um die Formatierung zu <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> unterstützen, müssen Sie die Methode überschreiben und einen eigenen Formatierungscode angeben.

## <a name="enabling-support-for-reformatting"></a>Aktivieren der Unterstützung für Neuformatierungen

Um die Formatierung zu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> unterstützen, `true` muss der `EnableFormatSelection` Parameter des Parameters beim Registrieren Ihres VSPackage festgelegt werden. Dadurch wird <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> die `true`Eigenschaft auf festgelegt. Die <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Methode gibt den Wert dieser Eigenschaft zurück. Wenn true zurückgegeben <xref:Microsoft.VisualStudio.Package.ViewFilter> wird, <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>ruft die Klasse die auf.

## <a name="implementing-reformatting"></a>Implementieren von Neuformatierungen

Um eine Neuformatierung zu implementieren, <xref:Microsoft.VisualStudio.Package.Source> müssen Sie eine <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> Klasse von der Klasse ableiten und die Methode überschreiben. Das <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Objekt beschreibt die Zuspannen, und das <xref:Microsoft.VisualStudio.Package.EditArray> Objekt enthält die an der Spanne vorgenommenen Bearbeitungen. Beachten Sie, dass diese Spanne das gesamte Dokument sein kann. Da jedoch wahrscheinlich mehrere Änderungen an der Spanne vorgenommen werden, sollten alle Änderungen in einer einzigen Aktion rückgängig gemacht werden können. Um dies zu tun, <xref:Microsoft.VisualStudio.Package.CompoundAction> umschließen Sie alle Änderungen in einem Objekt (siehe Abschnitt "Verwenden der CompoundAction-Klasse" in diesem Thema).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird sichergestellt, dass nach jedem Komma in der Auswahl ein einzelnes Leerzeichen vorhanden ist, es sei denn, auf das Komma folgt eine Registerkarte oder befindet sich am Ende der Zeile. Nachgestellte Leerzeichen nach dem letzten Komma in einer Zeile werden gelöscht. Weitere Informationen finden Sie im Abschnitt "Verwenden der CompoundAction-Klasse" <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> in diesem Thema, um zu sehen, wie diese Methode von der Methode aufgerufen wird.

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

## <a name="using-the-compoundaction-class"></a>Verwenden der CompoundAction-Klasse

Alle Neuformatierungen für einen Codeabschnitt sollten in einer einzigen Aktion rückgängig gemacht werden können. Dies kann mit <xref:Microsoft.VisualStudio.Package.CompoundAction> einer Klasse erreicht werden. Diese Klasse umschließt eine Reihe von Bearbeitungsvorgängen für den Textpuffer in einen einzigen Bearbeitungsvorgang.

### <a name="example"></a>Beispiel

Hier ist ein Beispiel für <xref:Microsoft.VisualStudio.Package.CompoundAction> die Verwendung der Klasse. Im Beispiel im Abschnitt "Implementieren der Unterstützung für formatieren" `DoFormatting` in diesem Thema finden Sie ein Beispiel für die Methode.

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

## <a name="see-also"></a>Weitere Informationen

- [Funktionen von Legacysprachdiensten](legacy-language-service-features1.md)
