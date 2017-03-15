---
title: "QuickInfo in einem Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eine QuickInfo Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
  - "IntelliSense-QuickInfo"
  - "Sprachdienste [Verwaltetes Paketframework], IntelliSense-QuickInfo"
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# QuickInfo in einem Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IntelliSense\-QuickInfo zeigt Informationen über einen Bezeichner in der Datenquelle, wenn der Benutzer die Einfügemarke in den Bezeichner setzt und wählt **Quick Info** aus der **IntelliSense** Menü oder den Mauszeiger über einen Bezeichner enthält. Dadurch wird eine QuickInfo mit Informationen zu den Bezeichner angezeigt. Diese Informationen besteht normalerweise aus der Typ des Bezeichners. Wenn das Debugging\-Modul aktiv ist, kann diese Informationen den aktuellen Wert enthalten. Das Debugging\-Modul stellt Ausdruckswerte, während der Sprachdienst nur Bezeichner behandelt.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Um weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
 Die verwalteten Paket Framework \(MPF\) Sprache Dienstklassen bieten vollständige Unterstützung für die IntelliSense\-QuickInfo\-QuickInfo anzeigen. Sie müssen lediglich lediglich stellen den Text angezeigt werden soll, und aktivieren die Funktion "QuickInfo".  
  
 Der anzuzeigende Text erhalten Sie durch Aufrufen der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \-Methode Parser analysiert Grund Wert <xref:Microsoft.VisualStudio.Package.ParseReason>. Aus diesem Grund teilt dem Parser zum Abrufen der Typinformationen \(oder angemessenen in der QuickInfo angezeigt werden\) für den Bezeichner an der Position, die gemäß den <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. Das <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt wird an übergeben haben die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode.  
  
 Der Parser muss analysieren, alles bis zu der Position in der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt, um die Typen von allen Bezeichnern bestimmen. Dann muss der Parser den Bezeichner an der Position der Parse\-Anforderung abzurufen. Der Parser muss übergeben Sie abschließend die Tool Tip\-Daten zugeordnet, um die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt, damit das Objekt zurückgeben des Texts aus kann die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> Methode.  
  
## Aktivieren der Funktion "QuickInfo"  
 Um die Funktion "QuickInfo" zu aktivieren, müssen Sie festlegen der `CodeSense` und `QuickInfo` benannte Parameter von der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Diese Attribute die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> und <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> Eigenschaften.  
  
## Implementieren die Funktion "QuickInfo"  
 Die <xref:Microsoft.VisualStudio.Package.ViewFilter> \-Klasse behandelt die IntelliSense\-QuickInfo\-Vorgang. Bei der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse erhält die <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl, die Ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \-Methode mit der Analyse Grund des <xref:Microsoft.VisualStudio.Package.ParseReason> und die Position der Einfügemarke zum Zeitpunkt der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl gesendet wurde. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser muss dann analysieren die Quelle bis zur angegebenen Position und analysieren den Bezeichner am angegebenen Speicherort zu bestimmen, welche in der QuickInfo angezeigt.  
  
 Die meisten Parsern führen Sie eine anfängliche Analyse der gesamte Quelldatei und speichert die Ergebnisse in eine Analysestruktur. Die vollständige Analyse erfolgt, wenn <xref:Microsoft.VisualStudio.Package.ParseReason> an übergeben <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode. Andere Arten der Analyse können dann die Analysestruktur verwenden, um die gewünschten Informationen zu erhalten.  
  
 Z. B. die Analyse Wert für den Grund der <xref:Microsoft.VisualStudio.Package.ParseReason> finden Sie die Kennung am Quellspeicherort und in der Analysestruktur zum Abrufen der Informationen zum Nachschlagen können. Diese Typinformationen übergeben, die <xref:Microsoft.VisualStudio.Package.AuthoringScope> \-Klasse und wird zurückgegeben, indem Sie die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> Methode.