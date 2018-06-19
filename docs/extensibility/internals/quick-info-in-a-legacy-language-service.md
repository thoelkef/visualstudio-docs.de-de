---
title: QuickInfo auf einen Legacy-Sprachdienst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdfe9bfb9063828a90dd9cdf3452ca3684ff0a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132148"
---
# <a name="quick-info-in-a-legacy-language-service"></a>QuickInfo auf einen Legacy-Sprachdienst
IntelliSense-QuickInfo zeigt Informationen über einen Bezeichner in der Quelle, wenn der Benutzer die Einfügemarke im Bezeichner positioniert und wählt **Quick Info** aus der **IntelliSense** Menü oder hält die Maus der Cursor über einen Bezeichner. Dadurch wird eine QuickInfo mit Informationen über die Bezeichner angezeigt werden. Diese Informationen besteht in der Regel des Typs ab. Wenn Sie das Debugmodul aktiv ist, kann diese Informationen den aktuellen Wert enthalten. Debugging-Modul liefert Ausdruckswerte, während der Sprachdienst nur Bezeichner behandelt.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
 Die verwaltete Package Framework (MPF) Sprache Dienstklassen bieten vollständige Unterstützung für die IntelliSense-QuickInfo-QuickInfo anzeigen. Alles, was Sie tun müssen ist, geben Sie den Text angezeigt werden, und die QuickInfo-Funktion aktivieren.  
  
 Der anzuzeigende Text abgerufen wird, durch Aufrufen der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser mit dem Analysieren Grund Wert <xref:Microsoft.VisualStudio.Package.ParseReason>. Aus diesem Grund weist den Parser zum Abrufen der Typinformationen (bzw. dem entsprechenden, in der QuickInfo angezeigt werden) für den Bezeichner auf die im angegebenen Speicherort der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. Die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt ist, was an übergeben wurde die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode.  
  
 Der Parser muss analysieren, alles, was bis zu der Position in der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt, um die Typen von alle Bezeichner zu ermitteln. Klicken Sie dann muss der Parser den Bezeichner an der Position der Parse-Anforderung abzurufen. Der Parser muss übergeben Sie abschließend das Tool Tip-Daten zugeordnet, Bezeichner, der die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt, damit dieses Objekt zurückgeben des Texts aus kann die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> Methode.  
  
## <a name="enabling-the-quick-info-feature"></a>Aktivieren des Features Quick Info  
 Um die QuickInfo-Funktion aktivieren zu können, müssen Sie festlegen der `CodeSense` und `QuickInfo` benannte Parameter von der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Legen Sie diese Attribute die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> und <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> Eigenschaften.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementieren die QuickInfo-Funktion  
 Die <xref:Microsoft.VisualStudio.Package.ViewFilter> -Klasse behandelt den IntelliSense-QuickInfo-Vorgang. Bei der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse erhält die <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> -Befehl, der die Klasse ruft der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode mit dem Grund der Analyse von <xref:Microsoft.VisualStudio.Package.ParseReason> und die Position des Caretzeichens zum Zeitpunkt der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl gesendet wurde. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser muss analysieren Sie die Quelle bis zur angegebenen Position und analysieren Sie den Bezeichner am angegebenen Speicherort zu bestimmen, welche in der QuickInfo angezeigt.  
  
 Die meisten Parsern führen Sie eine erste Analyse der gesamten Quelldatei und speichert die Ergebnisse in einem Analysestruktur. Die vollständige Analyse erfolgt, wenn <xref:Microsoft.VisualStudio.Package.ParseReason> übergeben <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode. Andere Arten der Analyse können dann die Analysestruktur verwenden, um die gewünschten Informationen abzurufen.  
  
 Z. B. die Analyse Wert für den Grund des <xref:Microsoft.VisualStudio.Package.ParseReason> in die Analysestruktur zum Abrufen der Informationen zum Suchen und finden den Bezeichner an den Quellspeicherort. Diese Typinformationen übergeben, die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, und wird zurückgegeben, durch die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> Methode.