---
title: Syntax-Färbung in benutzerdefinierten Editoren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699339"
---
# <a name="syntax-coloring-in-custom-editors"></a>Syntaxfarben in benutzerdefinierten Editoren
Visual Studio Environment SDK-Editoren, einschließlich des Kerneditors, verwenden Sprachdienste, um bestimmte syntaktische Elemente zu identifizieren und sie mit bestimmten Farben für eine bestimmte Dokumentansicht anzuzeigen.

## <a name="colorization-requirements"></a>Farbanforderungen
 Alle Editoren, die den Colorizer eines Sprachdienstes implementieren, müssen:

1. Verwenden Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> ein Objekt, das implementiert wird, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> um den zu kolorierenden Text und ein Objekt zu verwalten, das implementiert wird, um eine Dokumentansicht des Textes bereitzustellen.

2. Rufen Sie eine Schnittstelle zu einem bestimmten Sprachdienst ab, indem Sie den Dienstanbieter des VSPackage mithilfe der identifizierenden GUID des Sprachdiensts abfragen.

3. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Sie die Methode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>des Objekts auf, das implementiert. Diese Methode ordnet den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Sprachdienst der Implementierung zu, die das VSPackage zum Verwalten des zu kolorierenden Textes verwendet.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Core Editor Verwendung des Colorizers eines Sprachdienstes
 Wenn ein Sprachdienst mit einem Colorizer von einer Instanz des Kerneditors abgerufen wird, erfolgt das Parsen und Rendern von Text durch den Colorizer eines Sprachdienstes automatisch, ohne dass weitere Eingriffe Ihrerseits erforderlich sind.

 Die IDE transparent:

- Ruft den Colorizer nach Bedarf auf, um Text zu analysieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>und zu analysieren, wie er in der Implementierung von hinzugefügt oder geändert wird.

- Stellt sicher, dass die anzeige, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> die von der von der Implementierung bereitgestellt wird, aktualisiert und mit den vom Colorizer zurückgegebenen Informationen neu gezeichnet wird.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nicht-Kern-Editor-Nutzung des Colorizers eines Sprachdienstes
 Nicht-Kern-Editorinstanzen können auch den Syntaxfarbisierungsdienst eines Sprachdiensts verwenden, müssen jedoch den Colorizer des Diensts explizit abrufen und anwenden und ihre Dokumentansichten selbst neu zeichnen.

 Dazu muss ein Nicht-Kern-Editor:

1. Abrufen des Colorizer-Objekts <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> eines Sprachdienstes <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>(das implementiert und ). Das VSPackage tut dies, indem es die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode auf der Schnittstelle des Sprachdienstes aufruft.

2. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Sie die Methode auf, um anzufordern, dass eine bestimmte Textspanne koloriert wird.

     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode gibt ein Array von Werten zurück, einen für jeden Buchstaben in der Textspanne, die koloriert wird. Außerdem wird die Textspanne als ein bestimmter Typ von befärbbaren Elements identifiziert, z. B. als Kommentar, Schlüsselwort oder Datentyp.

3. Verwenden Sie die von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zurückgegebenen Farbinformationen, um den Text neu zu malen und anzuzeigen.

> [!NOTE]
> Zusätzlich zur Verwendung des Colorizers eines Sprachdienstes kann ein VSPackage den allgemeinen Textfarbmechanismus für Visual Studio Environment SDK verwenden. Weitere Informationen zu diesem Mechanismus finden Sie unter [Verwenden von Schriftarten und Farben](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="see-also"></a>Weitere Informationen

- [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren von Syntaxfarben](../extensibility/internals/implementing-syntax-coloring.md)
- [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Benutzerdefinierte einfärbbare Elemente](../extensibility/internals/custom-colorable-items.md)
