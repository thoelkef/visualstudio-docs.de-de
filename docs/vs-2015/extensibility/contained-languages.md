---
title: Enthaltenen Sprachen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20a42d614278413e4e6ee09ecacdf842ccee878d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662244"
---
# <a name="contained-languages"></a>Enthaltene Sprachen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*Enthaltenen Sprachen* sind Sprachen, die von anderen Sprachen enthalten sind. Z. B. HTML-Code im [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Webseiten enthalten u. u. [!INCLUDE[csprcs](../includes/csprcs-md.md)] oder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Skripts. Eine Dual-Language-Architektur ist erforderlich, für den ASPX-Datei-Editor, IntelliSense, farbige syntaxhervorhebung und andere-Bearbeitungsfeatures für die der HTML-Code und die verwendete Skriptsprache bereitzustellen.  
  
## <a name="implementation"></a>Implementierung  
 Die wichtigste Schnittstelle, die für enthaltene Sprachen implementiert werden müssen ist die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Diese Schnittstelle wird von einer beliebigen Sprache implementiert, die in eine primäre Sprache gehostet werden können. Er bietet Zugriff auf des Sprachdiensts Farbauswahl textansichtsfilter und primäre Sprache-Dienst-ID. Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> ermöglicht Ihnen die Erstellung einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Die folgenden Schritte gezeigt, wie eine enthaltene Sprache zu implementieren:  
  
1.  Verwendung `QueryService()` die Sprache, die Dienst-ID und die Schnittstellen-ID des abzurufenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> Methode zum Erstellen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Übergeben Sie ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -Schnittstelle, eine oder mehrere [der Artikel IDs](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Schnittstelle.  
  
3.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> -Schnittstelle, die das pufferkoordinatorobjekt für Text ist, enthält die grundlegenden Dienste, die erforderlich sind, um Positionen in einer primären Datei in den sekundären Sprachpuffer zuzuordnen.  
  
     Beispielsweise enthält die primäre Datei in einer einzelnen ASPX-Datei, die ASP, HTML und der gesamte Code, der enthalten ist. Die sekundäre Puffer enthält jedoch nur die enthaltenen Code zusammen mit Klassendefinitionen, auf dem sekundären Puffer eine gültige-Code-Datei zu erstellen. Der pufferkoordinator übernimmt die Aufgabe Koordinieren von Änderungen aus einem Puffer in den anderen.  
  
4.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> -Methode, die die primäre Sprache ist, weist der pufferkoordinator mit welcher Text innerhalb des Puffers auf den entsprechenden Text im sekundären Puffer zugeordnet ist.  
  
     Die Sprache in ein Array von übergibt die <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> Struktur, die derzeit nur ein primäres Zertifikat und einen sekundären Spanne enthält.  
  
5.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Methode und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> Methode die Zuordnung vom primären zum sekundären Puffer und umgekehrt bereit.
