---
title: Enthaltenen Sprachen | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbf2c63a66ba76b65d1caec2c5eed006d57fca0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109765"
---
# <a name="contained-languages"></a>Enthaltenen Sprachen

*Enthaltenen Sprachen* sind Sprachen, die von anderen Sprachen enthalten sind. Z. B. HTML-Code im [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Webseiten enthalten u. u. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Skripts. Eine Dual-Language-Architektur ist erforderlich, damit die ASPX-Datei-Editor den HTML-Code und die verwendete Skriptsprache IntelliSense, Einfärbung und andere-Bearbeitungsfeatures bereit.

## <a name="implementation"></a>Implementierung

Am wichtigsten Sie für enthaltenen Sprachen implementieren müssen diese Schnittstelle ist die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Diese Schnittstelle wird von einer beliebigen Sprache implementiert, die in eine primäre Sprache gehostet werden können. Er ermöglicht den Zugriff der Sprachdienst Colorizer, Ansichtsfilter Text und Hauptsprache Dienst-ID. Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> ermöglicht Ihnen die Erstellung einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Die folgenden Schritte zeigen Ihnen, wie eine eigenständige Sprache implementiert werden:

1.  Verwendung `QueryService()` die Sprache, die Dienst-ID und der Schnittstellen-ID der abzurufenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Zum Erstellen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle, rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> Methode. Übergeben Sie ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle, eine oder mehrere [der Artikel IDs](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>), und ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Schnittstelle.

3.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> -Schnittstelle, die der Koordinator TextBuffer-Objekt ist, enthält die grundlegenden Dienste, die erforderlich sind, um Positionen in einer primären Datei in der sekundären Sprache Puffer zuzuordnen.

     Beispielsweise enthält die primäre Datei in einer einzelnen ASPX-Datei der ASP-Seite, HTML und den Code aus, der enthalten ist. Die sekundäre Puffer enthält jedoch nur die darin enthaltenen Code zusammen mit Klassendefinitionen, die sekundären Puffer eine gültige Codedatei vornehmen. Der Puffer-Koordinator verarbeitet die Arbeit von Änderungen aus einem Puffer in den anderen koordinieren.

4.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Methode, die die primäre Sprache ist, weist der Koordinator Puffer Text innerhalb des Puffers für den entsprechenden Text im sekundären Puffers zugeordnet ist.

     Die Sprache übergibt ein Array von der <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> -Struktur, die derzeit nur einen primären und sekundären überspannende enthält.

5.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Methode und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> Methode geben Sie die Zuordnung vom primären zum sekundären Puffer und umgekehrt.