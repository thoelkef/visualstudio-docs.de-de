---
title: Syntaxfarben in benutzerdefinierten Editoren | Microsoft-Dokumentation
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
ms.openlocfilehash: ff717c8586e22d82a79344dd3c134c604f868d10
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316649"
---
# <a name="syntax-coloring-in-custom-editors"></a>Syntaxfarben in benutzerdefinierten Editoren
Visual Studio-Umgebung SDK-Editoren, einschließlich der Kern-Editor, verwenden Sie Sprachdienste bestimmte syntaktische Elemente zu identifizieren und mit angegebenen Farben für eine angegebene Dokumentenansicht anzeigen.

## <a name="colorization-requirements"></a>Farbliche Kennzeichnung von Anforderungen
 Alle Editoren, die einer editortooloptionsseite des Sprachdiensts Farbauswahl implementieren müssen:

1. Verwenden Sie ein Objekt, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> zum Verwalten der Text, der einzufärbenden und ein Objekt, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zum Dokument anzeigen des Texts.

2. Erhalten Sie eine Schnittstelle zu einem bestimmten Sprachdienst, durch die VSPackage Dienstanbieter, die mit den Sprachen des Diensts identifizierende GUID Abfragen.

3. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode die objektimplementierung <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Diese Methode ordnet den Sprachdienst mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> -Implementierung, die das VSPackage verwendet, um den Text zu verwalten, die farbig markiert werden.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Verwendung einer Editortooloptionsseite des Sprachdiensts Farbauswahl-Kern-Editor
 Wenn ein Sprachdienst mit einem Farbauswahl von einer Instanz von der Kern-Editor, für die Analyse und Rendern von Text von einer editortooloptionsseite des Sprachdiensts Farbauswahl abgerufen wird, wird automatisch ohne weiteren Eingriff Ihrerseits.

 Die IDE transparent:

- Ruft die Farbauswahl je nach Bedarf zu analysieren, Text zu analysieren, da sie hinzugefügt oder werden, in der Implementierung von geändert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

- Stellt sicher, dass die Anzeige der Dokumentenansicht gebotenen vom die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Implementierung wird aktualisiert und neu gezeichnet, anhand der Informationen, die von der Farbauswahl zurückgegeben.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nicht zum Kern-Editor-Nutzung einer Editortooloptionsseite des Sprachdiensts Farbauswahl
 Nicht-Kern-Editor-Instanzen können sich auch auf einer editortooloptionsseite des Sprachdiensts Syntax farbliche Kennzeichnung von Dienst, aber sie müssen explizit abrufen und Anwenden des Diensts Farbauswahl, und neu zu zeichnen ihren Ansichten des Dokuments selbst.

 Zu diesem Zweck müssen ein nicht zum Kern-Editor ein:

1. Abrufen einer editortooloptionsseite des Sprachdiensts Farbauswahl-Objekt (implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Das VSPackage wird durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> -Methode für den Sprachdienst-Schnittstelle.

2. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode, um anzufordern, dass es sich bei ein bestimmter Textabschnitt farbig markiert werden.

     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode gibt ein Array von Werten zurück, eine für jeden Buchstaben im Text umfassen farbig hervorgehoben wird. Er gibt außerdem den Textabschnitt als einen bestimmten Typ kolorierbaren Elements, z. B. einen Kommentar, Schlüsselwort oder Datentyp.

3. Verwenden Sie die farbliche Kennzeichnung von Informationen vom <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> neu zu zeichnen und den Text anzuzeigen.

> [!NOTE]
> Zusätzlich zur Verwendung einer editortooloptionsseite des Sprachdiensts Farbauswahl, können eine VSPackage die allgemeinen Text syntaxkennzeichnung Mechanismus für Visual Studio-Umgebung SDK verwenden. Weitere Informationen zu diesen Mechanismus, finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Siehe auch

- [Syntaxfarben in einem Legacysprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementieren von Syntaxfarben](../extensibility/internals/implementing-syntax-coloring.md)
- [Vorgehensweise: Verwenden von integrierten einfärbbaren Elementen](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Benutzerdefinierte einfärbbare Elemente](../extensibility/internals/custom-colorable-items.md)