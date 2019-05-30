---
title: Bewährte Methoden für die Implementierung eines Quellcodeverwaltungs-Plug-in | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89bc4065a450f82b3cdec33e94f4e17ea700d3c7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352207"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Bewährte Methoden für die Implementierung eines Quellcodeverwaltungs-Plug-in
Die folgenden technischen Details können Sie zuverlässig ein Quellcodeverwaltungs-Plug-in implementieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="memory-management-issues"></a>Verwaltung von Arbeitsspeicherproblemen
 In den meisten Fällen wird die integrierte Entwicklungsumgebung (IDE), die der Aufrufer ist, gibt und belegt Arbeitsspeicher. Das Quellcodeverwaltungs-Plug-Ins gibt Zeichenfolgen und andere Elemente im vom Aufrufer reservierte Puffer zurück. Ausnahmen werden in Beschreibungen bestimmter Funktionen aufgeführt, in dem sie auftreten.

## <a name="arrays-of-file-names"></a>Arrays von Dateinamen
 Wenn ein Array von Dateien übergeben wird, wird er nicht als Array von Dateinamen zusammenhängenden übergeben. Es wird als ein Array von Zeigern in Dateinamen übergeben. Z. B. in der [SccGet](../extensibility/sccget-function.md), die Dateinamen werden durch Übergeben der `lpFileNames` -Parameter, in denen `lpFileNames` ist tatsächlich ein Zeiger auf eine `char **`. `lpFileNames`[0] ist ein Zeiger auf den Vornamen, `lpFileNames`[1] ein Zeiger auf den zweiten Namen und So weiter.

## <a name="large-model"></a>Umfangreiches Modell
 Alle Zeiger sind 32-Bit, sogar von 16-Bit-Betriebssystemen unterstützt.

## <a name="fully-qualified-paths"></a>Vollqualifizierte Pfade
 In dem Dateinamen müssen oder Verzeichnisse als Argumente angegeben werden, da vollqualifizierte Pfade oder UNC-Pfade, ohne das abschließende umgekehrte Schrägstriche. Es ist die Verantwortung für das Quellcodeverwaltungs-Plug-in diese relativen Pfade, wenn also eine Voraussetzung für das zugrunde liegende Quellcodeverwaltungssystem zu übersetzen.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Geben Sie einen vollqualifizierten Pfad für die registrierte DLL
 Die IDE lädt DLLs nicht mehr über relative Pfade (z. B. *.\NewProvider.dll*). Ein vollständiger Pfad der DLL muss angegeben werden (z. B. *C:\Providers\NewProvider.dll*). Diese Anforderung erhöht die Sicherheit der IDE durch das Laden von nicht autorisierten oder dessen Identität angenommen wurde quellcodeverwaltung DLLs zu verhindern.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Überprüfen Sie bei der Installation von Ihrer quellcodeverwaltung-Plug-In für einen vorhandenen VSSCI-Plug-in
 Ein Benutzer, die Ihre quellcodeverwaltung-Plug-in installieren möchte möglicherweise bereits ein vorhandene Datenquellen-Steuerelement-Plug-in auf dem Computer installiert. Das Installationsprogramm (Setup) für das plug-in die Erstellung sollte bestimmen, ob vorhandene Werte für die entsprechenden Registrierungsschlüssel vorhanden sind. Wenn dieser Schlüssel bereits festgelegt sind, sollte Ihr Installationsprogramm über den Benutzer bitten, ob als das Standard-Quellcodeverwaltungs-Plug-Ins das plug-in registrieren, und ersetzen, die bereits installiert ist.

## <a name="error-result-codes-and-reporting"></a>Ergebnis-Fehlercodes und berichterstellung
 Die `SCC_OK` Rückgabewert Code für eine Source-Control-Funktion gibt an, dass der Vorgang für alle Dateien erfolgreich war. Wenn der Vorgang fehlschlägt, wird erwartet, dass die aufgetretenen letzten Fehlercode zurückgegeben.

 Die Regel für die berichterstellung ist, dass im Falle ein Fehlers in der IDE, die IDE für die berichterstellung er verantwortlich ist. Wenn ein Fehler in der Quellcode-Verwaltungssystems auftritt, ist das Quellcodeverwaltungs-Plug-In für gemeldet verantwortlich. Z. B. **derzeit sind keine Dateien ausgewählt** würde von der IDE, gemeldet werden, während **diese Datei ist bereits ausgecheckt** vom plug-in ausgegeben.

## <a name="the-context-structure"></a>Die Context-Struktur
 Während des Aufrufs der [SccInitialize](../extensibility/sccinitialize-function.md), der Aufrufer übergibt die `ppvContext` -Parameter, der eine nicht initialisierte Handle für eine "void" ist. Das Quellcodeverwaltungs-Plug-in kann diesen Parameter ignorieren oder eine Struktur jeglicher Art zuordnen und die übergebene Zeiger einen Zeiger auf dieser Struktur abgelegt. Die IDE diese Struktur nicht interpretieren, aber übergibt einen Zeiger auf diese Struktur in jeden anderen Aufruf in das plug-in. Diese wertvollen Cache stellt Kontextinformationen bereit, an das plug-in, globale Zustandsinformationen zu verwalten, die funktionsaufrufübergreifend hinweg beibehalten werden soll, ohne die Verwendung von globalen Variablen verwendet werden kann. Das plug-in ist verantwortlich für das Freigeben der Struktur in einem Aufruf der [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Wenn im-Plug-in wird die `SCC_CAP_REENTRANT` bit in der [SccInitialize](../extensibility/sccinitialize-function.md) (insbesondere in der `lpSccCaps` Parameter), mehrere Kontext Strukturen werden verwendet, um alle Projekte nachzuverfolgen, die geöffnet sind.

## <a name="bitflags-and-other-command-options"></a>Bitflags und andere Befehlsoptionen
 Für jeden Befehl z. B. die [SccGet](../extensibility/sccget-function.md), die IDE kann angeben, dass viele Optionen, die das Verhalten des Befehls zu ändern.

 Die API unterstützt bestimmte Optionen von der IDE durch Festlegen der `fOptions` Parameter. Diese Optionen werden in beschrieben [von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md) sowie die Befehle, die sie betreffen. Im Allgemeinen sind diese Optionen, die für die der Benutzer nicht aufgefordert werden sollen.

 Die meisten Benutzer konfigurierbare Einstellungsoptionen sind nicht auf diese Weise definiert, da sie von Quellcodeverwaltungs-Plug-ins variieren. Daher die empfohlene Methode ist ein **erweitert** Schaltfläche. Beispielsweise sind in der **erhalten** Dialogfeld zeigt nur Informationen, die er versteht, aber es zeigt auch die IDE eine **erweitert** Schaltfläche, wenn das plug-in verfügt über Optionen für diesen Befehl. Klickt der Benutzer die **erweitert** Schaltfläche, die IDE-Aufrufe der [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) das Quellcodeverwaltungs-Plug-in mit Informationen, z. B. Bitflags oder einen Datums-/Uhrzeitwert benutzeraufforderung zu aktivieren. Das plug-in gibt diese Informationen in einer Struktur, die während des übergeben wird die `SccGet` Befehl.

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)