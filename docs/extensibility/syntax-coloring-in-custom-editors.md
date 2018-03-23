---
title: Syntaxfarben in benutzerdefinierten Editoren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 699479d162bd4f2f0d37cc43f80ff40a53e5cb44
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="syntax-coloring-in-custom-editors"></a>Syntaxfarben in benutzerdefinierten Editoren
Visual Studio-Umgebung SDK-Editoren, darunter auch die Core-Editor mithilfe Sprachdienste bestimmte syntaktische Elemente zu identifizieren und mit angegebenen Farben für ein bestimmtes Dokument-Ansicht anzeigen.

## <a name="colorization-requirements"></a>Farbliche Kennzeichnung von Anforderungen
 Alle Editoren implementieren einen Sprachdienst Colorizer müssen:

1.  Verwenden Sie ein Objekt, durch <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> zum Verwalten der Text, der farbig hervorgehoben werden und ein Objekt, durch <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> eine Dokumentenansicht des Texts angeben.

2.  Eine Schnittstelle für einen bestimmten Sprachdienst durch Abfragen der VSPackage-Dienstanbieter mit den Sprachen Dienst identifizierende GUID zu erhalten.

3.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode das Objekt, durch <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Diese Methode ordnet der Sprachdienst mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Implementierung, die das VSPackage verwendet, um den Text zu verwalten, die farbig hervorgehoben werden.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Core-Editor einen Sprachdienst Colorizer Verwendung
 Wenn ein Sprachdienst mit einem Colorizer von einer Instanz von den Core-Editor, für die Analyse und das rendering von Text durch einen Sprachdienst Colorizer abgerufen wird, erfolgt automatisch ohne weiteren Eingriff Ihrerseits.

 Die IDE transparent:

-   Ruft die Colorizer nach Bedarf, zu analysieren und Analysieren von Text, da sie hinzugefügt oder werden, in der Implementierung der geändert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

-   Stellt sicher, dass die Anzeige von die Dokumentansicht gebotenen bereitgestellten der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Implementierung aktualisiert und neu gezeichnet, anhand der Informationen, die von der Colorizer zurückgegeben wird.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nicht-Core-Editor Verwendung einen Sprachdienst Colorizer
 Nicht-Core Editorinstanzen können auch einen Sprachdienst Syntax farbliche Kennzeichnung Dienst, jedoch müssen explizit abgerufen werden und der Dienst Colorizer anwenden und ihre Dokumentansichten selbst neu gezeichnet werden.

 Zu diesem Zweck müssen ein nicht-Core-Editor ein:

1.  Rufen Sie einen Sprachdienst Colorizer Objekt (implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Das VSPackage wird dies durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode auf der Sprachdienst-Schnittstelle.

2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um anzufordern, dass eine bestimmte Textabschnitts farbig hervorgehoben werden.

     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode gibt ein Array von Werten, eine für jedes Buchstabens im Text erstreckt farbig hervorgehoben wird. Außerdem ermittelt es des Textabschnitts als eine bestimmte Art von färbbare Element, z. B. einen Kommentar, Schlüsselwort oder Datentyp.

3.  Verwenden Sie die farbliche Kennzeichnung Informationen zurückgegebenes <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> , zu zeichnen und der Anzeigetext.

> [!NOTE]
> Zusätzlich zur Verwendung des Sprachdiensts Colorizer, können eine VSPackage den Mechanismus zur allgemeinen Visual Studio-Umgebung SDK Text TAB-TASTE verwenden. Weitere Informationen zu diesem Mechanismus finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Siehe auch

- [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren von Syntaxfarben](../extensibility/internals/implementing-syntax-coloring.md)
- [Gewusst wie: Verwenden von integrierten einfärbbaren Elementen](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Benutzerdefinierte einfärbbare Elemente](../extensibility/internals/custom-colorable-items.md)