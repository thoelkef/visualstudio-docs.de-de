---
title: Schnelle Informationen in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705944"
---
# <a name="quick-info-in-a-legacy-language-service"></a>QuickInfo in einem Legacysprachdienst
IntelliSense Quick Info zeigt Informationen zu einem Bezeichner in der Quelle an, wenn der Benutzer entweder die Einstellte in den Bezeichner legt und **Quick Info** aus dem **IntelliSense-Menü** auswählt oder den Mauszeiger über dem Bezeichner hält. Dadurch wird ein QuickInfo mit Informationen zum Bezeichner angezeigt. Diese Informationen bestehen in der Regel aus dem Bezeichnertyp. Wenn das Debugmodul aktiv ist, können diese Informationen den aktuellen Wert enthalten. Das Debugmodul stellt Ausdruckswerte zur Verfügung, während der Sprachdienst nur Bezeichner verarbeitet.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von QuickInfo-Tooltips](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

 Die MPF-Sprachdienstklassen (Managed Package Framework) bieten vollständige Unterstützung für die Anzeige des IntelliSense Quick Info-Tooltipps. Alles, was Sie tun müssen, ist, den anzuzeigenden Text zu liefern und die Schnellinfo-Funktion zu aktivieren.

 Der anzuzeigende Text wird durch <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Aufrufen des Methodenparsers <xref:Microsoft.VisualStudio.Package.ParseReason>mit dem Parse-Grundwert von erhalten. Aus diesem Grund wird der Parser aufgefordert, die Typinformationen (oder was auch immer in der Quick <xref:Microsoft.VisualStudio.Package.ParseRequest> Info-Tooltipp angezeigt werden soll) für den Bezeichner an der im Objekt angegebenen Position abzusuchen. Das <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt ist das, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> was an die Methode übergeben wurde.

 Der Parser muss alles bis zur <xref:Microsoft.VisualStudio.Package.ParseRequest> Position im Objekt analysieren, um die Typen aller Bezeichner zu bestimmen. Dann muss der Parser den Bezeichner am Speicherort der Parse-Anforderung abrufen. Schließlich muss der Parser die diesem Bezeichner <xref:Microsoft.VisualStudio.Package.AuthoringScope> zugeordneten QuickInfo-Daten an <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> das Objekt übergeben, damit das Objekt den Text von der Methode zurückgeben kann.

## <a name="enabling-the-quick-info-feature"></a>Aktivieren der Quick Info-Funktion
 Um die Schnellinfo-Funktion zu `CodeSense` aktivieren, müssen Sie die und `QuickInfo` benannten Parameter der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>festlegen. Diese Attribute legen <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> die und Eigenschaften fest.

## <a name="implementing-the-quick-info-feature"></a>Implementieren der Quick Info-Funktion
 Die <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse verarbeitet den IntelliSense Quick Info-Vorgang. Wenn <xref:Microsoft.VisualStudio.Package.ViewFilter> die Klasse <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> den Befehl empfängt, ruft die Klasse die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode mit dem Analysegrund <xref:Microsoft.VisualStudio.Package.ParseReason> und der Position der Einstellte zum Zeitpunkt <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> der Sendezeit auf. Der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methodenparser muss dann die Quelle bis zur angegebenen Position analysieren und dann den Bezeichner an der angegebenen Position analysieren, um zu bestimmen, was in der Quick Info-Toolspitze angezeigt werden soll.

 Die meisten Parser führen eine erste Analyse der gesamten Quelldatei durch und speichern die Ergebnisse in einer Analysestruktur. Die vollständige Analyse wird <xref:Microsoft.VisualStudio.Package.ParseReason> durchgeführt, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wenn sie an die Methode übergeben wird. Andere Arten der Analyse können dann den Parse-Baum verwenden, um die gewünschten Informationen zu erhalten.

 Der Wert für die Analyse <xref:Microsoft.VisualStudio.Package.ParseReason> von kann z. B. den Bezeichner an der Quellposition finden und in der Analysestruktur nachschlagen, um die Typinformationen abzusondern. Diese Typinformationen werden dann <xref:Microsoft.VisualStudio.Package.AuthoringScope> an die Klasse <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> übergeben und von der Methode zurückgegeben.
