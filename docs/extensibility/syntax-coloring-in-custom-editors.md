---
title: Syntax Farbgebung in benutzerdefinierten Editoren | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4302f463d93776d17be0251e6194375c15adc19
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718766"
---
# <a name="syntax-coloring-in-custom-editors"></a>Syntaxfarben in benutzerdefinierten Editoren
Visual Studio-Umgebungs-SDK-Editoren, einschließlich des Kern-Editors, verwenden Sprachdienste, um bestimmte syntaktische Elemente zu identifizieren und diese mit den angegebenen Farben für eine bestimmte Dokument Ansicht anzuzeigen.

## <a name="colorization-requirements"></a>Farbige Anforderungen
 Alle Editoren, die die Farbgebung eines sprach Dienstanbieter implementieren, müssen:

1. Verwenden Sie ein Objekt, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementiert, um den Text für die Farbgebung zu verwalten, und ein Objekt, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementiert, um eine Dokument Ansicht des Texts bereitzustellen.

2. Rufen Sie eine Schnittstelle zu einem bestimmten Sprachdienst ab, indem Sie den Dienstanbieter des VSPackages mithilfe der identifizierenden GUID des sprach Dienstanbieters Abfragen.

3. Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>-Methode des Objekts auf, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementiert. Diese Methode verknüpft den Sprachdienst mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>-Implementierung, die das VSPackage verwendet, um den Text zu verwalten, der farbig markiert werden soll.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Basis-Editor-Verwendung der Farbgebung eines sprach Dienstanbieter
 Wenn ein Sprachdienst mit einer Farbauswahl von einer Instanz des Kern-Editors abgerufen wird, werden die Text-und Renderingvorgänge durch die Farbgebung eines sprach Dienstanbieter automatisch durchgeführt, ohne dass ein weiterer Eingriff erforderlich ist.

 Die IDE ist transparent:

- Ruft die Farbgebung nach Bedarf auf, um Text zu analysieren und zu analysieren, da er in der Implementierung von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> hinzugefügt oder geändert wird.

- Stellt sicher, dass die Anzeige, die von der von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>-Implementierung bereitgestellten Dokument Ansicht bereitgestellt wird, mithilfe der von der Farbgebung zurückgegebenen Informationen aktualisiert und neu gezeichnet wird.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nicht-Kern-Editor-Verwendung der Farbgebung eines sprach Dienstanbieter
 Nicht-Kern-Editor-Instanzen können auch den Syntax Farb Erfassungs Dienst eines sprach Dienstanbieter verwenden. Sie müssen jedoch explizit die Farbgebung des dienstanwenders abrufen und anwenden und die Dokument Sichten selbst neu zeichnen.

 Zu diesem Zweck muss ein nicht-Kern-Editor folgende Aktionen ausführen:

1. Abrufen des Farb Erfassers Objekts eines sprach dienstanders (das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> implementiert). Das VSPackage bewirkt dies durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>-Methode für die-Schnittstelle des sprach Dienstanbieter.

2. Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>-Methode auf, um anzufordern, dass ein bestimmter Textabschnitt farbig markiert werden soll.

     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>-Methode gibt ein Array von-Werten zurück, eines für jeden Buchstaben in der Text Spanne, die farbig markiert wird. Außerdem wird der Textabschnitt als eine bestimmte Art von Kolon-Element, z. b. ein Kommentar, ein Schlüsselwort oder ein Datentyp, identifiziert.

3. Verwenden Sie die von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zurückgegebenen farbliche Informationen, um den Text neu zu zeichnen und anzuzeigen.

> [!NOTE]
> Zusätzlich zur Verwendung der Farbgebung eines sprach Dienstanbieter kann ein VSPackage auswählen, dass der Text Farb Mechanismus für das allgemeine Visual Studio-Umgebungs-SDK verwendet werden soll. Weitere Informationen zu diesem Mechanismus finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Siehe auch

- [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren von Syntaxfarben](../extensibility/internals/implementing-syntax-coloring.md)
- [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Benutzerdefinierte einfärbbare Elemente](../extensibility/internals/custom-colorable-items.md)