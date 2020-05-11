---
title: Quellcodeverwaltung Plug-In-API-Funktionen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699922"
---
# <a name="source-control-plug-in-api-functions"></a>API-Funktionen von Quellcodeverwaltungs-Plug-Ins
Die Quellcodeverwaltungs-Plug-In-API bietet die folgenden Funktionen, die vom Quellcodeverwaltungs-Plug-In gemäß dieser API implementiert werden müssen. Die Signaturen der einzelnen Funktionen und die Semantik, die den Bitflags und anderen Parametern zugeordnet ist, werden in dieser Referenz ausführlich beschrieben.

## <a name="initialization-and-housekeeping-functions"></a>Initialisierungs- und Housekeeping-Funktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Schließt ein Projekt.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Fordert den Benutzer auf, erweiterte Optionen für den angegebenen Befehl zu erhalten.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Gibt die Version des Quellcodeverwaltungs-Plug-Ins zurück.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialisiert das Quellcodeverwaltungs-Plug-In. Sie wird einmal für jede Instanz des Plug-Ins aufgerufen.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Öffnet ein Projekt.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Eine generische Funktion, die zum Festlegen einer Vielzahl von Optionen verwendet wird. Jede Option `SCC_OPT_xxx` beginnt mit und verfügt über einen eigenen definierten Satz von Werten.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wird einmal aufgerufen, wenn ein Quellcodeverwaltungs-Plug-In getrennt werden muss.|

## <a name="core-source-control-functions"></a>Kernquellensteuerungsfunktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Fügt dem Quellcodeverwaltungssystem ein Array von Dateien hinzu, die durch vollqualifizierte Pfadnamen angegeben sind.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Ermöglicht es dem Benutzer, nach Dateien zu suchen, die sich bereits im Quellcodeverwaltungssystem befinden, und diese Dateien dann zum Teil des aktuellen Projekts zu machen.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Überprüft ein Array von Dateien.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Checkt ein Array von Dateien aus.|
|[SccDiff](../extensibility/sccdiff-function.md)|Zeigt die Unterschiede zwischen der Datei des lokalen Benutzers an, die durch einen vollqualifizierten Pfadnamen angegeben wird, und der Version unter Quellcodeverwaltung.|
|[SccGet](../extensibility/sccget-function.md)|Ruft eine schreibgeschützte Kopie einer Gruppe von Dateien ab.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Überprüft den Status von Dateien, nach denen `SccQueryInfo`der Anrufer gefragt hat (via ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Bewirkt, dass das Quellcodeverwaltungs-Plug-In den Benutzer zu einem Projektpfad auffordert, der für das Plug-In sinnvoll ist.|
|[SccHistory](../extensibility/scchistory-function.md)|Zeigt den Verlauf für ein Array voll qualifizierter lokaler Dateinamen an.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Überprüft die Liste der Dateien auf ihren aktuellen Status. Darüber hinaus verwendet `pfnPopulate` die Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht den Kriterien für die `nCommand`entspricht.|
|[SccProperties](../extensibility/sccproperties-function.md)|Zeigt die Eigenschaften einer vollqualifizierten Datei an.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Überprüft eine Liste voll qualifizierter Dateien auf ihren aktuellen Status.|
|[SccRemove](../extensibility/sccremove-function.md)|Entfernt das Array voll qualifizierter Dateien aus dem Quellcodeverwaltungssystem.|
|[SccRename](../extensibility/sccrename-function.md)|Benennt die angegebene Datei in einen neuen Namen im Quellcodeverwaltungssystem um.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Greift auf die gesamte Bandbreite der Funktionen des Quellcodeverwaltungssystems zu.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Macht das Auschecken eines Arrays von Dateien auf.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funktionen, die zusätzliche Funktionen unterstützen (Version 1.2 der Quellcodeverwaltungs-Plug-In-API)
 Diese Gruppe von Funktionen definiert die zusätzliche Funktionalität, die in Version 1.2 der Quellcodeverwaltungs-Plug-In-API enthalten ist. Sie bieten Zugriff auf erweiterte Quellcodeverwaltungsfunktionen und -funktionen.

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Startet einen Stapelvorgang.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Erstellt ein Unterprojekt mit dem angegebenen Namen unter einem vorhandenen übergeordneten Projekt.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Zeigt die Unterschiede zwischen dem Verzeichnis des lokalen Benutzers an, das durch einen vollqualifizierten Pfadnamen und den Speicherort der Quellcodeverwaltungsdatenbank angegeben wird.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Untersucht eine Liste voll qualifizierter Verzeichnisse auf ihren aktuellen Status.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Beendet einen Stapelvorgang.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Gibt den übergeordneten Pfad des angegebenen Projekts zurück (das Projekt muss vorhanden sein).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Überprüft, ob mehrere Auscheckungen für eine Datei zulässig sind.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Überprüft, ob das Plug-In MSSCCPRJ erstellt. SCC-Dateien.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funktionen, die erweiterte Funktionen unterstützen (Version 1.3 der Quellcodeverwaltungs-Plug-In-API)
 Diese Gruppe von Funktionen definiert die zusätzlichen Funktionen, die in Version 1.3 der Quellcodeverwaltungs-Plug-In-API enthalten sind. Sie bieten Zugriff auf erweiterte Quellcodeverwaltungsfunktionen und -funktionen.

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Fügt dem aktuellen Projekt eine Liste von Dateien aus der Quellcodeverwaltung hinzu.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Ruft eine Liste von Dateien aus der Quellcodeverwaltung ohne Benutzeroberfläche ab.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Ruft eine Liste von Dateien in der Quellcodeverwaltung ab, die sich von den lokalen Dateien unterscheiden.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Ruft Flags ab, die erweiterte Funktionen angeben, die vom Quellcodeverwaltungs-Plug-In unterstützt werden.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Ruft benutzerspezifische Optionen ab.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Untersucht eine Liste von Verzeichnissen und Dateien in einem Projekt oder Projekten, die sich unter Quellcodeverwaltung befinden. Jeder gefundene Verzeichnis- und Dateiname wird an eine Rückruffunktion übergeben.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Untersucht Namensänderungen, die an einer Liste von Dateien vorgenommen wurden. Jeder Dateiname wird an eine Rückruffunktion mit seinem Änderungsstatus übergeben.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: scc.h

 (Im Environment SDK allgemein enthalten Ordner, standardmäßig *[Laufwerk]*,,Programmdateien, VSIP 8.0, EnvSDK, common, inc; auch im VSIP-Ordner mit dem MSSCCI-Beispiel, *[Laufwerk]*, Programmdateien, VSIP 8.0, MSSCCI) angegeben.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)
