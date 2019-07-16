---
title: Source-Control-Plug-in-API-Funktionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02e2c7ee92ab138de7bee0d58835898f3bd0a58b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160614"
---
# <a name="source-control-plug-in-api-functions"></a>API-Funktionen von Quellcodeverwaltungs-Plug-Ins
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Source-Plug-in-API bietet die folgenden Funktionen, die durch das Quellcodeverwaltungs-Plug-in in Übereinstimmung mit dieser API implementiert werden muss. Die Signaturen für jede Funktion und die Semantik von die Bitflags zugeordnet, und andere Parameter sind in dieser Referenz ausführlich beschrieben.  
  
## <a name="initialization-and-housekeeping-functions"></a>Initialisierung und Verwaltungsfunktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Schließt ein Projekt.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Fordert den Benutzer für die erweiterten Optionen für den angegebenen Befehl.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Gibt die Version des Datenquellen-Steuerelements-Plug-in zurück.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialisiert das Quellcodeverwaltungs-Plug-in. Es wird einmal für jede Instanz des Plug-Ins aufgerufen.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Öffnet ein Projekt.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Eine generische Funktion verwendet, um eine Vielzahl von Optionen festzulegen. Jede Option beginnt mit `SCC_OPT_xxx` und verfügt über einen eigenen definierten Satz von Werten.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wird aufgerufen, wenn wenn ein Quellcodeverwaltungs-Plug-in getrennt werden muss.|  
  
## <a name="core-source-control-functions"></a>Core Quellcodeverwaltungsfunktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Fügt ein Array von Dateien, die durch den vollqualifizierten Pfadnamen für die Quellcode-Verwaltungssystems angegeben.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Ermöglicht dem Benutzer, Dateien zu suchen, die bereits in der Quellcode-Verwaltungssystems sind, und stellen Sie dann diese Dateien Teil des aktuellen Projekts.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Überprüft, in ein Array von Dateien.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Checkt ein Array von Dateien aus.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Zeigt die Unterschiede zwischen den lokalen Benutzer-Datei, die durch einen Namen für den vollqualifizierten Pfad und die Version in der quellcodeverwaltung angegeben.|  
|[SccGet](../extensibility/sccget-function.md)|Ruft eine schreibgeschützte Kopie eines Satzes von Dateien.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Überprüft den Status der Dateien, die der Aufrufer über gestellt hat (über `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Bewirkt, dass das Quellcodeverwaltungs-Plug-in, um den Benutzer für einen Projektpfad zu aufzufordern, die für das angegebene plug-in verwertbar ist.|  
|[SccHistory](../extensibility/scchistory-function.md)|Zeigt den Verlauf für ein Array von vollqualifizierten Dateinamen, lokale an.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Untersucht die Liste der Dateien für ihren aktuellen Status an. Darüber hinaus verwendet der `pfnPopulate` Funktion, um den Aufrufer darüber zu benachrichtigen, wenn eine Datei nicht die Kriterien für entspricht der `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Zeigt die Eigenschaften von einem vollständig qualifizierten Dateinamen.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Überprüft eine Liste der vollqualifizierten Dateien für ihren aktuellen Status an.|  
|[SccRemove](../extensibility/sccremove-function.md)|Entfernt das Array von vollqualifizierten Dateien aus dem Quellcodeverwaltungssystem.|  
|[SccRename](../extensibility/sccrename-function.md)|Benennt die angegebene Datei auf einen neuen Namen in das Quellcodeverwaltungssystem.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Greift auf das gesamte Spektrum an Funktionen des Quellcode-Verwaltungssystem.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Macht das Auschecken der ein Array von Dateien rückgängig.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funktionen, die zusätzliche Funktionen (Version 1.2 von die Source-Plug-in-API) zu unterstützen  
 Diese Gruppe von Funktionen definiert, die zusätzliche Funktionalität, die in Version 1.2 von die Source-Plug-in-API enthalten. Sie bieten Zugriff auf Erweiterte Quellcodeverwaltungsfeatures und Funktionen.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Startet einen Batchvorgang.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Erstellt ein Unterprojekt mit dem angegebenen Namen unter einem vorhandenen übergeordneten-Projekt.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Zeigt die Unterschiede zwischen dem lokalen Verzeichnis des Benutzers durch einen Namen für den vollqualifizierten Pfad und den Speicherort auf dem Quellcode-Datenbank angegeben.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Überprüft eine Liste der vollqualifizierten Verzeichnisse für ihren aktuellen Status an.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Beendet einen Batchvorgang.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Gibt übergeordneten Pfad des angegebenen Projekts (das Projekt muss vorhanden sein).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Überprüft, ob Mehrfaches Auschecken für eine Datei zulässig sind.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Überprüft, ob das plug-in MSSCCPRJ erstellen. SCC-Dateien.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funktionen, die Unterstützung der erweiterten Funktionalität (Version 1.3 von der Quelle-Plug-in-API)  
 Diese Gruppe von Funktionen definiert, die zusätzliche Funktionalität, die in der Quelle-Plug-in-API-Version 1.3 enthalten. Sie bieten Zugriff auf Erweiterte Quellcodeverwaltungsfeatures und Funktionen.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Fügt eine Liste von Dateien aus der quellcodeverwaltung für das aktuelle Projekt an.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Ruft eine Liste von Dateien aus der quellcodeverwaltung ohne Benutzeroberfläche ab.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Ruft eine Liste von Dateien in der quellcodeverwaltung, die sich aus den lokalen Dateien unterscheiden.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Ruft die Flags, die erweiterten Funktionen, die durch das Quellcodeverwaltungs-Plug-in unterstützt angeben.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Ruft die benutzerspezifischen Optionen ab.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Überprüft eine Liste von Verzeichnissen und Dateien in einem Projekt oder die Projekte, die unter quellcodeverwaltung stehen. Jeder Name Verzeichnis- und Dateinamen, die gefunden wird, eine Callback-Funktion übergeben.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Überprüft die Namensänderungen vorgenommen, um eine Liste der Dateien. Jeder Dateiname wird an eine Callback-Funktion mit den Status für Änderungen übergeben.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: scc.h  
  
 (Angegeben im SDK-Umgebung gemeinsam enthält Ordner standardmäßig *[Laufwerk]* \Program Files\VSIP 8.0\EnvSDK\common\inc; auch in der VSIP-Ordner mit dem MSSCCI-Beispiel angegeben *[Laufwerk]* \Programme Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)
