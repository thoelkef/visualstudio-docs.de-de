---
title: QuickInfo in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2fff27f665453ff1b722ec1ef061494d48361988
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927619"
---
# <a name="quick-info-in-a-legacy-language-service"></a>QuickInfo in einem Legacysprachdienst
IntelliSense-QuickInfo zeigt Informationen über einen Bezeichner in der Quelle, wenn der Benutzer entweder die Einfügemarke in die ID setzt und wählt **Quick Info** aus der **IntelliSense** Menü oder die Maus der Cursor über einen Bezeichner. Dadurch wird eine QuickInfo mit Informationen zu den Bezeichner angezeigt werden. Diese Informationen enthalten i. d. r. der Typ des Bezeichners. Wenn die Debug-Engine aktiv ist, kann diese Informationen den aktuellen Wert enthalten. Die Debug-Engine stellt Ausdruckswerte, während der Sprachdienst nur Bezeichner behandelt.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
 Die verwaltete Package Framework (MPF) Sprache Dienstklassen bieten vollständige Unterstützung zum Anzeigen der IntelliSense-QuickInfo-QuickInfo. Müssen Sie lediglich den Text angezeigt werden, und aktivieren die Funktion "QuickInfo" angeben.  
  
 Der anzuzeigende Text abgerufen wird, durch den Aufruf der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode-Parser, mit dem Analysieren Grund Wert <xref:Microsoft.VisualStudio.Package.ParseReason>. Aus diesem Grund teilt dem Parser abgerufen, die Typinformationen (oder was auch immer in der QuickInfo anzuzeigende geeignet ist) für den Bezeichner, an dem im angegebenen Speicherort der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. Die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt ist, was übergeben wurde die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode.  
  
 Der Parser muss alles, was bis zu die Position im Analysieren der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt, um die Typen von allen Bezeichnern zu ermitteln. Dann muss der Parser die Bezeichner an der Position der Analyse-Anforderung abrufen. Schließlich muss der Parser die Tool-Tip-Daten zugeordnet, Bezeichner, der übergeben der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt, damit dieses Objekt Text zurückgeben, kann die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> Methode.  
  
## <a name="enabling-the-quick-info-feature"></a>Aktivieren der Funktion "QuickInfo"  
 Um die Funktion "QuickInfo" zu aktivieren, müssen Sie festlegen der `CodeSense` und `QuickInfo` benannte Parameter, der die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Legen Sie diese Attribute die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> und <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> Eigenschaften.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementieren der Funktion "QuickInfo"  
 Die <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse verarbeitet, den IntelliSense-QuickInfo-Vorgang. Wenn der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse erhält die <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl, der die ruft der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode mit der Analyse Grund des <xref:Microsoft.VisualStudio.Package.ParseReason> und die Position des Textcursors zum Zeitpunkt der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl gesendet wurde. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser muss und analysieren Sie anschließend die Quelle bis zu der angegebenen Position und klicken Sie dann analysieren den Bezeichner am angegebenen Speicherort, um zu bestimmen, was in der QuickInfo angezeigt.  
  
 Die meisten Parser führen eine erste Analyse der gesamten Quelldatei und speichert die Ergebnisse in eine Analysestruktur. Die vollständige Analyse wird ausgeführt, wenn <xref:Microsoft.VisualStudio.Package.ParseReason> übergeben wird, um <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode. Andere Arten der Analyse können dann die Analysestruktur verwenden, um die gewünschten Informationen abzurufen.  
  
 Z. B. den ursachenwert Analyse der <xref:Microsoft.VisualStudio.Package.ParseReason> Suchen des Bezeichners am Quellspeicherort können, und suchen sie in der Struktur analysieren, um die Typinformationen zu erhalten. Diese Typinformationen übergeben, die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, und wird zurückgegeben, durch die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> Methode.