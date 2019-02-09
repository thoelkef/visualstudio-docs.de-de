---
title: Arbeitsbereiche und Sprachdienste in Visual Studio | Microsoft-Dokumentation
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929777"
---
# <a name="workspaces-and-language-services"></a>Arbeitsbereiche und Sprachdienste

Sprachdienste bieten ["Ordner öffnen"](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Benutzer die gleichen umfassenden Sprachfunktionen werden verwendet, um bei der Arbeit mit Projektmappen und Projekten. Aktivieren eines Sprachdiensts möglicherweise selbst basierend auf die Dateierweiterung oder den Inhalt eines geöffneten Dokuments, obwohl diesem Sprachdienst "lose Datei" auf die syntaxhervorhebung beschränkt ist. Weitere Informationen sind erforderlich, um eine reichhaltigere Erfahrung zu bieten, beim Bearbeiten von/Überprüfen von Quellcode. Jeder Sprachdienst verfügt über eine eigene API für die Initialisierung mit diesen zusätzlichen kontextbezogenen Daten für ein Dokument. Dies wird in der Regel von ein Projektsystem, verwaltet die eng, auf den Sprachdienst sowohl für das Buildsystem gekoppelt ist.

## <a name="initialization"></a>Initialisierung

In einem [Arbeitsbereich](workspaces.md), Sprachdienste werden initialisiert, indem ein <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> -Erweiterungspunkt an, die nur in diesem Sprachdienst spezialisiert und nicht bekannt ist, der die Erstellung von Builds. Auf diese Weise kann Besitzer einer Sprache des Diensts einen einzelnen öffnen-Ordner, die Erweiterung unabhängig davon, wie viele Muster befinden sich in Ordnern und Dateien für die Ausführung ihrer Compiler während eines Builds (z. B. MSBuild, Makefiles, usw.) verwalten. Wenn Dateien, die aus denen ein Kontext erstellt wurde, werden auf dem Datenträger geändert, und der Kontext aktualisiert wird, wird der aktualisierte Satz der dateikontexte des Sprachanbieters für den Dienst informiert. Der Dienstanbieter für die Sprache kann dann ein Modell aktualisieren.

Wenn ein Dokument im Editor geöffnet ist, berücksichtigt Visual Studio nur Sprache Dienstanbieter, die Kontext-Dateitypen erfordern für die eine übereinstimmende Datei Kontextanbieter gefunden werden kann. Es übergibt dann die Datei Kontext(e) aus der entsprechenden Anbieter an den Dienstanbieter für ausgewählte Sprache über `ILanguageServiceProvider.InitializeAsync`. Der Dienstanbieter für die Sprache mit Funktionsweise, dass Kontextdaten für die Datei ein Implementierungsdetail des Dienstanbieters Sprache ist, aber die erwartete Benutzeroberfläche eine umfangreichere Sprachdienst ist, Dokument geöffnet.

## <a name="using-ilanguageserviceprovider"></a>Verwenden von ILanguageServiceProvider

Der Sprachdienst benachrichtigt werden, wenn ein Kontext erstellt wird eine `ContextType` entspricht einer der der `SupportedContextTypes` Werte des Servers Sprache export-Attribut.

Um einen Sprachdienst zu unterstützen, müssen eine Erweiterung:

- Eine eindeutige `Guid`. Dies wird zum `SupportedContextTypes` Attribut Argumente und in eine `FileContext` Objekt.
- Language-Dateikontext
  - Anbieterfactory
    - `ExportFileContextProviderAttribute` Attribut, mit den oben generiert, die eindeutig `Guid` in `SupportedContextTypes`
    - Implementiert `IWorkspaceProviderFactory<IFileContextProvider>`
  - Anbieterimplementierung der `IFileContextProvider.GetContextsForFileAsync`
    - Erstellt ein neues `FileContext` mit der `contextType` Konstruktorargument als eindeutig generierten `Guid`
    - Verwenden der `Context` Eigenschaft der `FileContext` um zusätzliche Daten zu gewähren. der `ILanguageServiceProvider`
- Sprachdienst
  - Anbieterfactory
    - `ExportLanguageServiceProvider` Attribut, mit den oben generiert, die eindeutig `Guid` in `SupportedContextTypes`
    - Implementiert `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Anbieter
    - Implementiert `ILanguageServiceProvider`
    - Verwendung `ILanguageServiceProvider.InitializeAsync` Sprachdienste für die angegebenen Argumente aktivieren, wenn eine Datei geöffnet ist
    - Verwendung `ILanguageServiceProvider.UninitializeAsync` , deaktivieren Sprachdienste für die angegebenen Argumente aus, wenn eine Datei geschlossen wird

>[!WARNING]
>Die `ILanguageServiceProvider` Methoden durch den Arbeitsbereich auf dem Hauptthread aufgerufen werden können. Erwägen Sie die Planung von Arbeiten in einem anderen Thread aus, um zu vermeiden, Einführung in die Verzögerungen.

## <a name="language-server-protocol"></a>Sprachserverprotokoll

Die `Microsoft.VisualStudio.Workspace.*` APIs sind nicht die einzige Möglichkeit, den Sprachdienst im "Ordner öffnen" zu aktivieren. Eine weitere Option ist einen Sprache-Server verwenden. Weitere Informationen finden Sie Informationen zu den [Sprachserverprotokoll](language-server-protocol.md).

## <a name="related-interfaces"></a>Zugehörigen Schnittstellen

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> wird aufgerufen, wenn eine Datei mit übereinstimmenden Dateitypen geöffnet oder für die Bearbeitung geschlossen wird.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereich erstellen](workspace-build.md) -Buildsysteme für "Ordner öffnen" unterstützt z.B. MSBuild und Makefiles.