---
title: Neuformatieren von Code in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16130191eb6a4d8b6d7703a05aaf3271f8c739f5
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891123"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Neuformatieren von Code in einem Legacysprachdienst

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcode durch die Verwendung von Einzüge und Leerzeichen normalisieren neu formatiert werden kann. Dazu kann gehören, einfügen oder Entfernen von Leerzeichen oder Tabstopps am Anfang jeder Zeile, Hinzufügen neuer Zeilen zwischen den Zeilen oder Leerzeichen durch Tabstopps oder Tabstopps, Leerzeichen ersetzt.

> [!NOTE]
> Einfügen oder Löschen von Zeilenumbruchzeichen Marker, wie z. B. Haltepunkte und Lesezeichen auswirken kann, aber hinzufügen oder Entfernen von Leerzeichen oder Tabstopps wirkt sich nicht Marker.

Benutzer können einen neuformatierung Vorgang starten, indem Sie die Auswahl **Formatauswahl** oder **Dokument formatieren** aus der **erweitert** Menü auf der **Bearbeiten**Menü. Ein neuformatierung Vorgang kann auch ausgelöst werden, wenn ein Codeausschnitt oder ein bestimmtes Zeichen eingefügt wird. Beispielsweise wenn Sie eine schließende geschweifte Klammer in C# -Code eingeben, ist alles, was zwischen die entsprechende öffnende geschweifte Klammer und der schließenden geschweiften Klammer automatisch auf die richtige Ebene eingezogen.

Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sendet die **Formatauswahl** oder **Dokument formatieren** Befehl auf den Sprachdienst, der <xref:Microsoft.VisualStudio.Package.ViewFilter> -Klasse ruft die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.Source> Klasse. Zur Unterstützung der Formatierung, müssen Sie überschreiben, die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> -Methode, und geben Ihre eigenen codeformatierung.

## <a name="enabling-support-for-reformatting"></a>Aktivieren der Unterstützung für neu formatieren

Formatierung, unterstützen die `EnableFormatSelection` Parameter, der die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> muss festgelegt werden, um `true` beim Registrieren Ihres VSPackages. Hiermit wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> Eigenschaft `true`. Die <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Methode gibt den Wert dieser Eigenschaft zurück. Wenn "true" gibt die <xref:Microsoft.VisualStudio.Package.ViewFilter> -Klasse ruft die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.

## <a name="implementing-reformatting"></a>Implementieren von neu formatieren

Um neuformatierung zu implementieren, müssen Sie leiten eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source> Klasse, und überschreiben die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> Methode. Die <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Objekt beschreibt die Spanne, formatieren und die <xref:Microsoft.VisualStudio.Package.EditArray> -Objekt enthält, auf die Spanne vorgenommenen Bearbeitungen aus. Beachten Sie, dass diese Spanne das gesamte Dokument. Aber da es sich wahrscheinlich mehrere Änderungen an der Spanne, sollte alle Änderungen in einer einzigen Aktion rückgängig gemacht werden. Umschließen Sie zu diesem Zweck alle Änderungen in einem <xref:Microsoft.VisualStudio.Package.CompoundAction> Objekt (siehe Abschnitt "Verwenden der CompoundAction-Klasse", in diesem Thema).

### <a name="example"></a>Beispiel

Im folgende Beispiel wird sichergestellt, dass es ist ein einzelnes Leerzeichen nach jedem Komma in die Auswahl, wenn das Komma von einer Registerkarte gefolgt oder am Ende der Zeile. Leerzeichen nach das letzte Komma in einer Zeile werden gelöscht. Finden Sie im Abschnitt "Verwenden der CompoundAction-Klasse" in diesem Thema finden, wie diese Methode aufgerufen wird, aus der <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> Methode.

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

Alle der neuformatierung für einen Codeabschnitt ausgeführt sollte in einer einzigen Aktion rückgängig gemacht werden. Dies geschieht mithilfe einer <xref:Microsoft.VisualStudio.Package.CompoundAction> Klasse. Diese Klasse dient als Wrapper für einen Satz von Bearbeitungsvorgängen für den Textpuffer in einer einzelnen Bearbeitungsvorgang.

### <a name="example"></a>Beispiel

Hier ist ein Beispiel zur Verwendung der <xref:Microsoft.VisualStudio.Package.CompoundAction> Klasse. Siehe das Beispiel im Abschnitt "Implementieren von Unterstützung für Formatierung" in diesem Thema ein Beispiel für die `DoFormatting` Methode.

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

- [Funktionen von Legacysprachdiensten](legacy-language-service-features1.md)