---
title: Benutzerdefinierte färbbare Artikel | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708996"
---
# <a name="custom-colorable-items"></a>Benutzerdefinierte farbbare Artikel
Sie können die Liste der Typen für die Farbtierung, z. B. Schlüsselwörter und Kommentare, überschreiben, indem Sie benutzerdefinierte befärbbare Elemente als Teil Ihres Sprachdienstes implementieren.

## <a name="user-settings-of-colorable-items"></a>Benutzereinstellungen von befärbbaren Elementen
 Sie können das Dialogfeld **Schriftarten und Farben** anzeigen, indem Sie im Menü **Extras** **Optionen** und dann unter **Umgebung** **Schriftarten und Farben** auswählen. Wenn Sie eine Anzeige auswählen, z. **B. Texteditor** oder **Befehlsfenster,** werden im Listenfeld **Elemente anzeigen** alle befärbbaren Elemente für diese Anzeige angezeigt. Sie können die Schriftart, Größe, Vordergrundfarbe und Hintergrundfarbe für jedes befärbbare Element anzeigen und ändern. Ihre Auswahlmöglichkeiten werden in einem Cache in der Registrierung gespeichert und über den namendes farbiges Element zugegriffen.

## <a name="presentation-of-colorable-items"></a>Präsentation von befärbbaren Gegenständen
 Da die IDE Benutzerüberschreibungen von befärbten Elementen im Dialogfeld **Schriftarten und Farben** verarbeitet, müssen Sie nur jedes benutzerdefinierte befärbbare Element mit einem Namen angeben. Dieser Name wird in der Liste **Elemente anzeigen** angezeigt. Die befärbbaren Elemente werden in alphabetischer Reihenfolge angezeigt. Um die benutzerdefinierten farbbaren Elemente Ihres Sprachdienstes zu gruppieren, können Sie jeden Namen mit Ihrem Sprachnamen beginnen, z. B. **NewLanguage - Comment** und **NewLanguage - Keyword**.

> [!CAUTION]
> Sie sollten den Sprachnamen in den befärbten Elementnamen aufnehmen, um Kollisionen mit vorhandenen farbbaren Elementnamen zu vermeiden. Wenn Sie den Namen eines Ihrer befärbten Elemente während der Entwicklung ändern, müssen Sie den Cache zurücksetzen, der beim ersten Zugriff auf die befärbten Elemente erstellt wurde. Sie können den experimentellen Cache mit dem **CreateExpInstance-Tool** zurücksetzen, das mit dem Visual Studio SDK installiert wird, in der Regel im Verzeichnis:
>
> *C:-Programmdateien (x86) , Microsoft Visual Studio 14.0, VSSDK,VisualStudioIntegration, Tools, Bin*
>
> Um den Cache zurückzusetzen, geben Sie **CreateExpInstance /Reset**ein. Weitere Informationen **zu CreateExpInstance**finden Sie unter [CreateExpInstance utility](../../extensibility/internals/createexpinstance-utility.md).

 Auf das erste Element in der Liste der befärbten Elemente wird nie verwiesen. Das erste Element entspricht einem befärbbaren Elementindex von 0 und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] liefert immer die Standardtextfarben und -attribute für dieses Element. Der einfachste Weg, mit diesem nicht referenzierten Element umzugehen, besteht darin, als erstes Element ein platzhalterfarbenes Element in Ihrer Liste zu liefern.

## <a name="implement-custom-colorable-items"></a>Implementieren sie benutzerdefinierte befärbbare Elemente

1. Definieren Sie, was in Ihrer Sprache koloriert werden muss, z. B. Schlüsselwort, Operator und Bezeichner.

2. Erstellen Sie eine Aufzählung dieser befärbten Elemente.

3. Ordnen Sie den Tokentypen, die von einem Parser oder Scanner zurückgegeben werden, den aufgezählten Werten zu.

    Beispielsweise können die Werte, die die Tokentypen darstellen, die gleichen Werte in der benutzerdefinierten farbigen Elementenumeration sein.

4. Füllen Sie bei <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Implementierung der Methode in Ihrem Objekt die Attributliste mit den Werten aus Ihrer benutzerdefinierten farbbaren Elementaufzählung aus, die den Tokentypen entspricht, die vom Parser oder Scanner zurückgegeben werden.

5. Implementieren Sie in derselben <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Klasse, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> die Schnittstelle implementiert, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>die Schnittstelle und ihre beiden Methoden und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> .

6. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>-Schnittstelle.

7. Wenn Sie 24-Bit- oder hohe Farbwerte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> unterstützen möchten, implementieren Sie auch die Schnittstelle.

8. Erstellen Sie in Ihrem Sprachdienstobjekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> eine Liste, die Ihre Objekte enthält, eine für jedes farbbare Element, das Ihr Parser oder Scanner identifizieren kann.

    Sie können auf jedes Element in der Liste zugreifen, indem Sie den entsprechenden Wert aus der benutzerdefinierten auffärbbaren Elementaufzählung verwenden. Verwenden Sie die Enumerationswerte als Index in der Liste. Auf das erste Element in der Liste wird nie zugegriffen, da es dem Standardtextstil entspricht, der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] immer selbst verarbeitet wird. Sie können dies kompensieren, indem Sie ein befärbbares Element des Platzhalters am Anfang der Liste einfügen.

9. Geben Sie in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> der Implementierung der Methode die Anzahl der Elemente in der Liste der benutzerdefinierten befärbbaren Elemente zurück.

10. Geben Sie in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> der Implementierung der Methode das angeforderte befärbbare Element aus Ihrer Liste zurück.

    Ein Beispiel für das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> der und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>der Schnittstellen finden Sie unter .

## <a name="see-also"></a>Weitere Informationen
- [Modell eines älteren Sprachdienstes](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Syntaxfärbung in benutzerdefinierten Editoren](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Syntaxfarben in einem älteren Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren der Syntaxfärbung](../../extensibility/internals/implementing-syntax-coloring.md)
- [Gewusst wie: Verwenden Sie integrierte farbbare Elemente](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
