---
title: Arbeitsbereiche und Dienste für die Sprachen in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 551a621ab97c232970d6ef67da14379c5cdfbd46
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140806"
---
# <a name="workspaces-and-language-services"></a>Arbeitsbereiche und Dienste für Sprachen

Sprache Dienstleistungen können [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Benutzer die gleichen umfangreiche Sprachfunktionen werden verwendet, um bei der Arbeit mit Projektmappen und Projekten. Aktivieren eines Sprachdiensts möglicherweise selbst basierend auf die Dateierweiterung oder den Inhalt eines geöffneten Dokuments, obwohl diese "loose File"-Sprachdienst auf syntaxhervorhebung beschränkt ist. Zusätzliche Informationen benötigt eine umfangreichere Erfahrung zu bieten, beim Bearbeiten von/Überprüfen von Quellcode. Jeder Sprachdienst verfügt über eine eigene API für die Initialisierung mit diesen zusätzlichen Kontextdaten für ein Dokument. Dies wird in der Regel durch ein Projektsystem verwaltet die Sprachdiensts sowohl für das Buildsystem eng gekoppelt ist.

## <a name="initialization"></a>Initialisierung

In einem [Arbeitsbereich](workspaces.md), Sprachdienste werden initialisiert, indem ein <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> Erweiterungspunkt, der nur innerhalb des betreffenden Sprachdiensts spezialisiert und bekannt ist, den Build erstellen. Auf diese Weise kann der Besitzer eines Language Service einen einzelnen Ordner öffnen Erweiterung unabhängig davon, wie viele Muster befinden sich in Ordnern und Dateien für die Ausführung ihrer Compiler während eines Builds (z. B. MSBuild, Makefiles, usw.) verwalten. Wenn Dateien aus denen ein Kontext erstellt wurde, auf dem Datenträger geändert werden und der Dateikontext aktualisiert wird, wird der Dienstanbieter für die Sprache der aktualisierte Satz der Datei Kontexten benachrichtigt. Der Language-Dienstanbieter können Sie das Modell aktualisieren.

Wenn ein Dokument im Editor geöffnet wird, berücksichtigt Visual Studio nur Language Serviceanbieter, die Datei Kontexttypen erfordern für die eine entsprechende Datei Kontextanbieter gefunden werden kann. Es übergibt dann die Datei Namenskontext(e) aus der entsprechenden Anbieter an den Dienstanbieter ausgewählte Sprache über `ILangaugeServiceProvider.InitializeAsync`. Der Dienstanbieter Sprache mit Wirkungsweise, dass Kontextdaten für die Datei ein Implementierungsdetail des Dienstanbieters Sprache ist, aber die erwarteten Benutzeroberfläche eine umfangreichere Sprachdienst für diesen ist Dokument geöffnet.

## <a name="using-ilanguageserviceprovider"></a>Verwenden von ILanguageServiceProvider

Der Sprachdienst benachrichtigt werden, wenn ein Kontext erstellt wird eine `ContextType` , die mit einem der übereinstimmt. die `SupportedContextTypes` Werte des Servers Sprache export-Attribut.

Um einen Sprachdienst zu unterstützen, müssen eine Erweiterung:

- Eine eindeutige `Guid`. Hiermit werden für `SupportedContextTypes` -Attribut Argumente und in einem `FileContext` Objekt.
- Datei Sprachkontext
  - Anbieterfactory
    - `ExportFileContextProviderAttribute` Attribut mit den oben genannten eindeutig generiert `Guid` in `SupportedContextTypes`
    - Implementiert `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementierung des Anbieters `IFileContextProvider.GetContextsForFileAsync`
    - Erstellen Sie ein neues `FileContext` mit der `contextType` Konstruktorargument als eindeutig generierten `Guid`
    - Verwenden der `Context` Eigenschaft von der `FileContext` um zusätzliche Daten zu gewähren. der `ILanguageServiceProvider`
- -Sprachdienst
  - Anbieterfactory
    - `ExportLanguageServiceProvider` Attribut mit den oben genannten eindeutig generiert `Guid` in `SupportedContextTypes`
    - Implementiert `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Anbieter
    - Implementiert `ILanguageServiceProvider`
    - Verwendung `ILanguageServiceProvider.InitializeAsync` Language-Dienste für die bereitgestellten Argumente aktivieren, wenn eine Datei geöffnet wird
    - Verwendung `ILanguageServiceProvider.UninitializeAsync` deaktivieren Sie Dienste für die Sprachen für die angegebenen Argumente aus, wenn eine Datei geschlossen wird

>[!WARNING]
>Die `ILanguageServiceProvider` Methoden Arbeitsbereich auf der Haupt-Thread aufgerufen werden können. Sollten Sie planen die Arbeit in einem anderen Thread, vermeiden Sie unnötigen Benutzeroberfläche verzögert.

## <a name="language-server-protocol"></a>Language-Server-Protokoll

Die `Microsoft.VisualStudio.Workspace.*` APIs sind nicht die einzige Möglichkeit zum Aktivieren der Sprachdienst im geöffneten Ordner. Eine andere Möglichkeit ist die Verwendung ein Servers für die Sprache. Lesen Sie weitere Informationen zu den [Sprache Serverprotokoll](language-server-protocol.md).

## <a name="related-interfaces"></a>Verwandte Schnittstellen

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> wird aufgerufen, wenn eine Datei mit übereinstimmenden Dateitypen geöffnet oder für die Bearbeitung geschlossen wird.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereich Build](workspace-build.md) -Ordner öffnen unterstützt Buildsysteme wie MSBuild und Makefiles. 