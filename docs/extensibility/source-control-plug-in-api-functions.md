---
title: Source Control-Plug-in-API-Funktionen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a834c4352ea2444c2669a57f760ed373999b07dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-plug-in-api-functions"></a>Quellcodeverwaltungsfunktionen-Plug-in-API
Die Datenquellen-Steuerelement-Plug-in-API bietet die folgenden Funktionen, die von der quellcodeverwaltung-Plug-in in Übereinstimmung mit dieser API implementiert werden müssen. Die Signaturen für jede Funktion und die Semantik von der Bitflags zugeordnet ist und andere Parameter werden in dieser Referenz im Detail beschrieben.  
  
## <a name="initialization-and-housekeeping-functions"></a>Initialisierung und Verwaltungsfunktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Schließt ein Projekt.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Fordert den Benutzer für die erweiterten Optionen für den angegebenen Befehl.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Gibt die Version des Datenquellen-Steuerelements-Plug-in zurück.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialisiert das Quellsteuerelement-Plug-in. Sie wird einmal für jede Instanz des Plug-Ins aufgerufen werden.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Öffnet ein Projekt.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Eine generische Funktion verwendet, um eine Vielzahl von Optionen festzulegen. Jede Option beginnt mit `SCC_OPT_xxx` und weist einen eigenen definierten Satz von Werten.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wird aufgerufen, sobald Wenn ein Quellcodeverwaltungs-Plug-in nicht angeschlossen werden muss.|  
  
## <a name="core-source-control-functions"></a>Core-Quellcodeverwaltungsfunktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Fügt ein Array von Dateien, die durch den vollqualifizierten Pfadnamen für das Quellcodeverwaltungssystem angegeben.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Ermöglicht es dem Benutzer nach Dateien suchen, die bereits in das Quellcodeverwaltungssystem sind, und stellen Sie dann diese Dateien Teil des aktuellen Projekts.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Überprüft in ein Array von Dateien.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Checkt ein Array von Dateien.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Zeigt die Unterschiede zwischen den lokalen Benutzer-Datei, die durch einen voll gekennzeichneten Pfadnamen und die Version in der quellcodeverwaltung angegeben.|  
|[SccGet](../extensibility/sccget-function.md)|Ruft eine schreibgeschützte Kopie einer Reihe von Dateien.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Überprüft den Status der Dateien, die der Aufrufer über geforderten (über `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Bewirkt, dass das plug-in, das den Benutzer für eine Projektpfad aufzufordern, das für das angegebene plug-in verwertbar wird Quellsteuerelement.|  
|[SccHistory](../extensibility/scchistory-function.md)|Zeigt den Verlauf für ein Array von vollqualifizierten lokalen Dateinamen.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Überprüft die Liste der Dateien für ihren aktuellen Status an. Darüber hinaus verwendet der `pfnPopulate` Funktion, um den Aufrufer benachrichtigen, wenn eine Datei nicht den Kriterien entsprechen der `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Zeigt die Eigenschaften einer vollqualifizierten Datei.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Wertet eine Liste der vollqualifizierten Dateien für ihren aktuellen Status an.|  
|[SccRemove](../extensibility/sccremove-function.md)|Entfernt das Array von vollqualifizierten Dateien aus dem Quellcodeverwaltungssystem.|  
|[SccRename](../extensibility/sccrename-function.md)|Benennt die angegebene Datei einen neuen Namen in das Quellcodeverwaltungssystem.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Greift auf das gesamte Spektrum der Funktionen von dem Quellcodeverwaltungssystem aus.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Macht einen Auscheckvorgang eines Arrays von Dateien an.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funktionen, die Unterstützung zusätzlicher-Funktion (Version 1.2 von der Quelle Steuerelement-Plug-in-API)  
 Diese Gruppe von Funktionen definiert, die zusätzliche Funktionalität, die in Version 1.2 der Datenquellen-Steuerelement-Plug-in-API enthalten. Sie bieten Zugriff auf Erweiterte Funktionen der quellcodeverwaltung und Funktionen.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Startet einen Batchvorgang.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Erstellt ein Unterprojekt mit dem angegebenen Namen unter einem vorhandenen übergeordneten Projekt.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Zeigt die Unterschiede zwischen den lokalen Benutzer Directory durch einen voll gekennzeichneten Pfadnamen und der Speicherort für die Quelle Datenbank angegeben.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Wertet eine Liste der vollständig qualifizierte Verzeichnisse für ihren aktuellen Status an.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Beendet einen Batchvorgang.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Gibt die übergeordnete Pfad für das angegebene Projekt (das Projekt muss vorhanden sein).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Überprüft, ob Mehrfaches Auschecken einer Datei zulässig sind.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Überprüft, ob das plug-in MSSCCPRJ erstellt wird. SCC-Dateien.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funktionen, die erweiterte Funktionalität (Version 1.3 der Datenquellen-Steuerelement-Plug-in-API) unterstützen.  
 Diese Gruppe von Funktionen definiert, die zusätzliche Funktionalität, die in Version 1.3 der Datenquellen-Steuerelement-Plug-in-API enthalten. Sie bieten Zugriff auf Erweiterte Funktionen der quellcodeverwaltung und Funktionen.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Fügt eine Liste von Dateien aus der quellcodeverwaltung für das aktuelle Projekt.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Ruft eine Liste von Dateien aus der quellcodeverwaltung ohne Benutzeroberfläche ab.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Ruft eine Liste der Dateien in der quellcodeverwaltung, die sich aus den lokalen Dateien unterscheiden.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Ruft die Flags, die erweiterte Funktionen, die von der quellcodeverwaltung-Plug-in unterstützt angeben.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Ruft die Benutzer-spezifischen Optionen ab.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Überprüft eine Liste von Verzeichnissen und Dateien in einem Projekt oder in Projekten, die in der quellcodeverwaltung sind. Jeder Name Verzeichnis- und Dateinamen, die gefunden wird, eine Rückruffunktion übergeben.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Untersucht Namensänderungen versucht, eine Liste der Dateien an. Jeder Dateiname wird auf eine Rückruffunktion mit dem Änderungsstatus übergeben.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: scc.h  
  
 (Angegeben im SDK-Umgebung gemeinsam enthält Ordner standardmäßig *[Laufwerk]*\Program Files\VSIP 8.0\EnvSDK\common\inc; auch im Ordner "VSIP" mit dem MSSCCI-Beispiel bereitgestellten *[Laufwerk]*\Programme Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)