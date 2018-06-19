---
title: Bewährte Methoden für ein Quellcodeverwaltungs-Plug-in implementieren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5e9972b28d435f5cba360b2328ecdd6d18eb52e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106047"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Bewährte Methoden für die Implementierung ein Quellcodeverwaltungs-Plug-in
Die folgenden technischen Details können Sie die zuverlässig ein Quellcodeverwaltungs-Plug-in implementieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Verwaltung von Arbeitsspeicherproblemen  
 In den meisten Fällen der integrierten Entwicklungsumgebung (IDE), also den Aufrufer frei und belegt Speicher. Die Datenquellen-Steuerelements, das plug-in gibt Zeichenfolgen und andere Elemente im vom Aufrufer reservierte Puffer zurück. Ausnahmen sind in Beschreibungen bestimmter Funktionen aufgeführt, in dem sie auftreten.  
  
## <a name="arrays-of-file-names"></a>Arrays von Dateinamen  
 Wenn ein Array von Dateien übergeben wird, wird er nicht als Array von Dateinamen zusammenhängenden übergeben. Es wird als ein Array von Zeigern auf Dateinamen übergeben. Z. B. in der [SccGet](../extensibility/sccget-function.md), die Dateinamen werden durch Übergeben der `lpFileNames` -Parameter, in dem `lpFileNames` ist tatsächlich ein Zeiger auf eine `char **`. `lpFileNames`[0] ist ein Zeiger auf den Vornamen `lpFileNames`[1] ist ein Zeiger auf die zweite Name und So weiter.  
  
## <a name="large-model"></a>Umfangreiches Modell  
 Alle Zeiger sind 32 Bits, sogar auf 16-Bit-Betriebssystemen.  
  
## <a name="fully-qualified-paths"></a>Vollqualifizierte Pfade  
 Speicherort der Datei Namen oder Verzeichnisse als Argumente angegeben werden, muss es sich um voll qualifizierten Pfade oder UNC-Pfade, ohne den Endwert umgekehrte Schrägstriche. Es liegt die Verantwortung des Datenquellen-Steuerelements-Plug-in diese relativen Pfade Wenn also eine Anforderung mit dem zugrunde liegenden Quellcodeverwaltungssystem übersetzen.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Geben Sie einen vollqualifizierten Pfad für die registrierten DLL  
 Die IDE lädt die DLLs nicht mehr aus relative Pfade (beispielsweise.\NewProvider.dll). Ein vollständiger Pfad der DLL muss (z. B. C:\Providers\NewProvider.dll) angegeben werden. Diese Anforderung erhöht die Sicherheit der IDE, indem verhindert das Laden von nicht autorisierten oder dessen Identität angenommen wurde quellcodeverwaltung DLLs.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Überprüfen Sie bei der Installation als Quellcodeverwaltungs-Plug-In für eine vorhandene VSSCI-Plug-in  
 Ein Benutzer, der als Quellcodeverwaltungs-Plug-in installieren möchte möglicherweise bereits ein vorhandenen Datenquellen-Steuerelement-Plug-in auf dem Computer installiert. Das Installationsprogramm (Setup) für das plug-in, die Sie erstellen, entscheiden Sie, ob vorhandene Werte für die entsprechenden Registrierungsschlüssel vorhanden sind. Wenn diese Schlüssel bereits festgelegt sind, sollte das Installationsprogramm die Benutzer auffordern, angibt, ob als die Standard-Datenquellen-Steuerelement-Plug-Ins das plug-in registrieren, und Ersetzen Sie das Projekt, das bereits installiert ist.  
  
## <a name="error-result-codes-and-reporting"></a>Ergebnis-Fehlercodes und Reporting  
 Die `SCC_OK` Code für eine Quelle Steuerelement-Funktion gibt an, dass der Vorgang, für alle Dateien erfolgreich war zurückgegeben. Wenn der Vorgang fehlschlägt, wird davon ausgegangen, die zuletzt aufgetretenen Fehlercode zurückgegeben.  
  
 Die Regel für die Berichterstattung ist, tritt ein Fehler in der IDE auf, die IDE für gemeldet zuständig ist. Wenn ein Fehler in das Quellcodeverwaltungssystem auftritt, ist das Quellsteuerelement-Plug-In für gemeldet verantwortlich. Z. B. würde "keine Dateien sind derzeit ausgewählte" von der IDE gemeldet werden dagegen vom plug-in "Diese Datei bereits ausgecheckt ist" gemeldet worden wären.  
  
## <a name="the-context-structure"></a>Context-Struktur  
 Während des Aufrufs der [SccInitialize](../extensibility/sccinitialize-function.md), der Aufrufer übergibt die `ppvContext` Parameter, der eine nicht initialisierte Handle für ein "void" ist. Das Quellsteuerelement-Plug-in kann dieser Parameter ignoriert oder eine Struktur jeglicher Art zuordnen und den übergebenen Zeiger einen Zeiger auf dieser Struktur abgelegt werden können. Die IDE nicht interpretieren kann diese Struktur, aber einen Zeiger an diese Struktur in jeden anderen Aufruf in das plug-in übergeben. Dies wertvolle Cache stellt Kontextinformationen bereit, um das plug-in, dass es zum Verwalten von globalen Zustandsinformationen, die bei Funktionsaufrufen beibehält, ohne die Verwendung von globalen Variablen verwenden kann. Das plug-in ist verantwortlich für die Freigabe der Struktur auf einen Aufruf der [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Wenn im-Plug-in wird die `SCC_CAP_REENTRANT` bit in der [SccInitialize](../extensibility/sccinitialize-function.md) (insbesondere in den `lpSccCaps` Parameter), mehrere Kontext Strukturen werden verwendet, um alle Projekte zu verfolgen, die geöffnet sind.  
  
## <a name="bitflags-and-other-command-options"></a>Bitflags und andere Befehlsoptionen  
 Für jeden Befehl wie z. B. die [SccGet](../extensibility/sccget-function.md), geben Sie die IDE kann zahlreiche Optionen zur Verfügung, die das Verhalten des Befehls zu ändern.  
  
 Die API unterstützt bestimmte Optionen von der IDE durch Festlegen der `fOptions` Parameter. Diese Optionen werden in beschrieben [Bitflags verwendet wird, indem Sie bestimmte Befehle](../extensibility/bitflags-used-by-specific-commands.md) zusammen mit den Befehlen, die sie betreffen. Im Allgemeinen werden diese Optionen für die der Benutzer nicht aufgefordert werden möchten.  
  
 Die meisten Benutzer konfigurierbare Festlegen von Optionen sind nicht auf diese Weise definiert, denn sie zwischen Source Control-Plug-ins variieren. Aus diesem Grund empfohlen wird ein **erweitert** Schaltfläche. Für die Instanz, in der **abrufen** Dialogfeld zeigt nur Informationen, die er versteht, aber es zeigt auch die IDE eine **erweitert** Schaltfläche, wenn die Plug-in-Optionen für diesen Befehl verfügt. Wenn der Benutzer klickt der **erweitert** Schaltfläche, die IDE-Aufrufe der [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) So aktivieren Sie das Quellsteuerelement-Plug-in, um den Benutzer Informationen, z. B. Bitflags oder einen Datums-/Uhrzeitwert aufzufordern. Das plug-in gibt diese Informationen in einer Struktur, die während der zurück übergeben wird die `SccGet` Befehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)