---
title: "Gewusst wie: unterst&#252;tzen Gliederung im ein Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] reduzieren Definitionen Befehl"
  - "Language Services, unterstützen nur Definitionen-Befehl"
  - "ausgeblendeten Text reduzieren Definitionen-Befehl"
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: unterst&#252;tzen Gliederung im ein Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gliederung dient zum Erweitern oder reduzieren die verschiedenen Bereiche des Texts. Die Weise Gliederung wird verwendet, kann in verschiedenen Sprachen unterschiedlich definiert werden. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md).  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren der Gliederung finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
 Im folgenden veranschaulicht, wie mit diesem Befehl zu Ihrer Sprache zu unterstützen.  
  
### Zur Unterstützung der Gliederung  
  
1.  Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> in Ihrer Sprache Dienstobjekt.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> für das aktuelle Gliederungsrand Sitzungsobjekt neue Gliederungsbereiche hinzufügen.  
  
## Robuste Programmierung  
 Wenn ein Benutzer auswählt **Nur Definitionen** auf der **Gliederung** Menü, die IDE\-Aufrufe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> für Ihren Sprachdienst.  
  
 Wenn diese Methode aufgerufen wird, übergibt die IDE in einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Zeiger \(einen Zeiger auf einen Textpuffer\) und ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> \(ein Zeiger auf die aktuelle Gliederung Sitzung\).  
  
 Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Methode für mehrere Gliederungsbereiche durch Angabe dieser Regionen in den `rgOutlnReg` Parameter. Der `rgOutlnReg` \-Parameter ist eine <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> Struktur. Dadurch können Sie andere Merkmale der im verborgenen Bereich, z. B., ob ein bestimmter Bereich erweitert oder reduziert ist.  
  
> [!NOTE]
>  Achten Sie darauf, dass zum Ausblenden von neue\-Zeile\-Zeichen. Ausgeblendeten Text sollte ab dem Anfang der ersten Zeile mit dem letzten Zeichen der letzten Zeile in einem Abschnitt, sodass das letzte neue\-Zeile\-Zeichen angezeigt sein.  
  
## Siehe auch  
 [Gewusst wie: unterstützen ausgeblendeter Text in einem Legacy\-Sprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Gewusst wie: unterstützen erweiterte Gliederung in eine Legacy\-Sprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)