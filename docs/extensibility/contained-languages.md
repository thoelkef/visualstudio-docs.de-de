---
title: Enthaltenen Sprachen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8adf63eed436b5724fcdb32d86ffc7bfb2c1a40
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="contained-languages"></a>Enthaltenen Sprachen
*Enthaltenen Sprachen* sind Sprachen, die von anderen Sprachen enthalten sind. Z. B. HTML-Code im [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Webseiten enthalten u. u. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Skripts. Eine Dual-Language-Architektur ist erforderlich, damit die ASPX-Datei-Editor den HTML-Code und die verwendete Skriptsprache IntelliSense, Einfärbung und andere-Bearbeitungsfeatures bereit.  
  
## <a name="implementation"></a>Implementierung  
 Am wichtigsten Sie für enthaltenen Sprachen implementieren müssen diese Schnittstelle ist die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Diese Schnittstelle wird von einer beliebigen Sprache implementiert, die in eine primäre Sprache gehostet werden können. Er ermöglicht den Zugriff der Sprachdienst Colorizer, Ansichtsfilter Text und Hauptsprache Dienst-ID. Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> ermöglicht Ihnen die Erstellung einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Die folgenden Schritte zeigen Ihnen, wie eine eigenständige Sprache implementiert werden:  
  
1.  Verwendung `QueryService()` die Sprache, die Dienst-ID und der Schnittstellen-ID der abzurufenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> Methode zum Erstellen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Übergeben Sie ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Netzwerkschnittstelle, die Element-ID (eine oder mehrere der <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, oder <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>) und eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Schnittstelle.  
  
3.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> -Schnittstelle, die der Koordinator TextBuffer-Objekt ist, enthält die grundlegenden Dienste, die erforderlich sind, um Positionen in einer primären Datei in der sekundären Sprache Puffer zuzuordnen.  
  
     Beispielsweise enthält die primäre Datei in einer einzelnen ASPX-Datei der ASP-Seite, HTML und den Code aus, der enthalten ist. Die sekundäre Puffer enthält jedoch nur die darin enthaltenen Code zusammen mit Klassendefinitionen, die sekundären Puffer eine gültige Codedatei vornehmen. Der Puffer-Koordinator verarbeitet die Arbeit von Änderungen aus einem Puffer in den anderen koordinieren.  
  
4.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Methode, die die primäre Sprache ist, weist der Koordinator Puffer Text innerhalb des Puffers für den entsprechenden Text im sekundären Puffers zugeordnet ist.  
  
     Die Sprache übergibt ein Array von der <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> -Struktur, die derzeit nur einen primären und sekundären überspannende enthält.  
  
5.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Methode und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> Methode geben Sie die Zuordnung vom primären zum sekundären Puffer und umgekehrt.