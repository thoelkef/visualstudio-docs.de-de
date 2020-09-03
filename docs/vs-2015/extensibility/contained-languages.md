---
title: Enthaltene Sprachen | Microsoft-Dokumentation
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
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184281"
---
# <a name="contained-languages"></a>Enthaltene Sprachen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*Enthaltene Sprachen* sind Sprachen, die in anderen Sprachen enthalten sind. Beispielsweise kann HTML auf [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Seiten- [!INCLUDE[csprcs](../includes/csprcs-md.md)] oder- [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Skripts enthalten. Eine Architektur mit zwei Sprachen ist erforderlich, damit der ASPX-Datei-Editor IntelliSense, farbige Farbgebung und andere Bearbeitungsfunktionen sowohl für die HTML-als auch für die Skriptsprache bereitstellt.  
  
## <a name="implementation"></a>Implementierung  
 Die wichtigste Schnittstelle, die Sie für enthaltene Sprachen implementieren müssen, ist die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Diese Schnittstelle wird von jeder Sprache implementiert, die in einer primären Sprache gehostet werden kann. Sie ermöglicht den Zugriff auf die Farbgebung, den Text Ansichts Filter und die Dienst-ID des sprach Dienstanbieter. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>Mit können Sie eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle erstellen. In den folgenden Schritten wird gezeigt, wie Sie eine enthaltene Sprache implementieren:  
  
1. Verwenden `QueryService()` Sie, um die Sprachdienst-ID und die Schnittstellen-ID von zu erhalten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. Rufen Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> Methode zum Erstellen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle auf. Übergeben Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle, eine oder mehrere [Element-IDs](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) und eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Schnittstelle.  
  
3. Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Schnittstelle, bei der es sich um das Text Puffer Koordinator-Objekt handelt, stellt die grundlegenden Dienste bereit, die erforderlich sind, um Standorte in einer primären Datei dem Puffer der sekundären Sprache zuzuordnen.  
  
     In einer einzelnen ASPX-Datei enthält die primäre Datei z. b. ASP, HTML und sämtlichen Code, der enthalten ist. Der sekundäre Puffer enthält jedoch nur den enthaltenen Code sowie alle Klassendefinitionen, um den sekundären Puffer zu einer gültigen Codedatei zu machen. Der Puffer Koordinator verarbeitet das Koordinieren von Änderungen von einem Puffer zum anderen.  
  
4. Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Methode, bei der es sich um die primäre Sprache handelt, teilt dem Puffer Koordinator mit, welcher Text in seinem Puffer dem entsprechenden Text im sekundären Puffer zugeordnet ist.  
  
     Die Sprache übergibt ein Array der <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> -Struktur, die derzeit nur eine primäre und eine sekundäre Spanne enthält.  
  
5. Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> -Methode und die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> Methode stellen die Zuordnung vom primären zum sekundären Puffer bereit und umgekehrt.
