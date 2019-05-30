---
title: Enthaltenen Sprachen | Microsoft-Dokumentation
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d48232ffe6bdc4535f52ed3e2a66a18147352112
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341757"
---
# <a name="contained-languages"></a>Enthaltene Sprachen

*Enthaltenen Sprachen* sind Sprachen, die von anderen Sprachen enthalten sind. Z. B. HTML-Code im [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Webseiten enthalten u. u. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Skripts. Eine Dual-Language-Architektur ist erforderlich, damit die *aspx* Dateieditor bieten IntelliSense, farbige syntaxhervorhebung und Bearbeiten von anderen Funktionen für den HTML-Code und die verwendete Skriptsprache.

## <a name="implementation"></a>Implementierung

Die wichtigste Schnittstelle, die für enthaltene Sprachen implementiert werden müssen ist die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Diese Schnittstelle wird von einer beliebigen Sprache implementiert, die in eine primäre Sprache gehostet werden können. Er bietet Zugriff auf des Sprachdiensts Farbauswahl textansichtsfilter und primäre Sprache-Dienst-ID. Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> ermöglicht Ihnen die Erstellung einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle. Die folgenden Schritte gezeigt, wie eine enthaltene Sprache zu implementieren:

1. Verwendung `QueryService()` die Sprache, die Dienst-ID und die Schnittstellen-ID des abzurufenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2. Zum Erstellen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Schnittstelle, rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> Methode. Übergeben Sie ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -Schnittstelle, eine oder mehrere [der Artikel IDs](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>), und ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Schnittstelle.

3. Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> -Schnittstelle, die das pufferkoordinatorobjekt für Text ist, enthält die grundlegenden Dienste, die erforderlich sind, um Positionen in einer primären Datei in den sekundären Sprachpuffer zuzuordnen.

     Z. B. in einem einzelnen *aspx* -Datei, die primäre Datei enthält, die ASP, HTML und den Code aus, die enthalten sind. Sekundäre Puffer enthält jedoch nur die enthaltenen Code zusammen mit Klassendefinitionen, auf dem sekundären Puffer eine gültige-Code-Datei zu erstellen. Der pufferkoordinator übernimmt die Aufgabe Koordinieren von Änderungen aus einem Puffer in den anderen.

4. Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> -Methode, die die primäre Sprache ist, weist der pufferkoordinator mit welcher Text innerhalb des Puffers auf den entsprechenden Text im sekundären Puffer zugeordnet ist.

     Die Sprache in ein Array von übergibt die <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> Struktur, die derzeit nur ein primäres Zertifikat und einen sekundären Spanne enthält.

5. Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Methode und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> Methode die Zuordnung vom primären zum sekundären Puffer und umgekehrt bereit.