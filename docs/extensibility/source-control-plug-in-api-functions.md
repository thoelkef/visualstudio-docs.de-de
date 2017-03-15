---
title: "Source Control-Plug-in-API-Funktionen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins Funktionen"
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Source Control-Plug-in-API-Funktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Datenquellen\-Steuerelement\-Plug\-in\-API bietet die folgenden Funktionen, die durch das Quellcodeverwaltungs\-Plug\-in in Übereinstimmung mit dieser API implementiert werden muss. Die Signaturen für jede Funktion und die Semantik von der Bitflags zugeordnet und andere Parameter werden in dieser Referenz ausführlich beschrieben.  
  
## Initialisierung und Verwaltungsfunktionen  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Schließt ein Projekt.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Fordert den Benutzer um weitere Optionen für den angegebenen Befehl.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Gibt die Version des Datenquellen\-Steuerelements\-Plug\-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialisiert das Quellcodeverwaltungs\-Plug\-in. Es wird einmal für jede Instanz des Plug\-Ins aufgerufen.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Öffnet ein Projekt.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Eine generische Funktion verwendet, um eine Vielzahl von Optionen festzulegen. Jede Option beginnt mit `SCC_OPT_xxx` und verfügt über einen eigenen definierten Satz von Werten.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wird aufgerufen, sobald Wenn ein Quellcodeverwaltungs\-Plug\-in getrennt werden muss.|  
  
## Core Quellcodeverwaltungsfunktionen  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Fügt ein Array von Dateien, die durch den vollqualifizierten Pfadnamen für Quellcode\-Verwaltungssystem angegeben.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Ermöglicht es dem Benutzer nach Dateien suchen, die bereits im Quellcode\-Verwaltungssystem sind, und nehmen Sie dann diese Dateien Teil des aktuellen Projekts.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Ein Array von Dateien überprüft.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Checkt ein Array von Dateien.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Zeigt die Unterschiede zwischen den lokalen Benutzer\-Datei, die durch einen vollqualifizierten Pfad\-Namen und die Version unter Datenquellen\-Steuerelement angegeben.|  
|[SccGet](../extensibility/sccget-function.md)|Ruft eine schreibgeschützte Kopie eines Satzes von Dateien.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Überprüft den Status der Dateien, die der Aufrufer gefragt wurde \(über `SccQueryInfo`\).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Bewirkt, dass das Quellcodeverwaltungs\-Plug\-in, um den Benutzer für ein Projektpfad, den das plug\-in.|  
|[SccHistory](../extensibility/scchistory-function.md)|Zeigt den Verlauf für ein Array von voll qualifizierten lokalen Namen.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Untersucht die Liste der Dateien für den aktuellen Status an. Darüber hinaus verwendet die `pfnPopulate` Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht den Kriterien entsprechen der `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Zeigt die Eigenschaften einer vollständig qualifizierten Datei.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Überprüft eine Liste der vollqualifizierten Dateien für den aktuellen Status an.|  
|[SccRemove](../extensibility/sccremove-function.md)|Entfernt das Array von vollqualifizierten Dateien aus dem Quellcode\-Verwaltungssystem.|  
|[SccRename](../extensibility/sccrename-function.md)|Benennt die angegebene Datei in einen neuen Namen in das Quellcodeverwaltungssystem.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Greift auf die vollständige Palette der Funktionen von Quellcode\-Verwaltungssystem.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Macht einen Auscheckvorgang eines Arrays von Dateien.|  
  
## Funktionen, die zusätzliche Funktionen \(Version 1.2 der Source Control\-Plug\-in\-API\) unterstützen.  
 Diese Gruppe von Funktionen definiert, die zusätzliche Funktionalität in Version 1.2 der Source Control\-Plug\-in\-API enthalten. Sie bieten Zugriff auf Erweiterte Quellcodeverwaltungsfunktionen und Funktionen.  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Startet einen Batchvorgang.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Erstellt ein Unterprojekt mit dem angegebenen Namen unter einem vorhandenen übergeordneten Projekt.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Zeigt die Unterschiede zwischen dem Verzeichnis des lokalen Benutzers durch einen vollqualifizierten Pfadnamen und der Speicherort für die Quelle Datenbank angegeben.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Überprüft eine Liste der vollqualifizierten Verzeichnisse für den aktuellen Status an.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Beendet einen Batchvorgang.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Gibt die übergeordnete Pfad für das angegebene Projekt \(das Projekt muss vorhanden sein\).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Überprüft, ob Mehrfaches Auschecken einer Datei zulässig sind.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Überprüft, ob das plug\-in MSSCCPRJ erstellt wird. SCC\-Dateien.|  
  
## Funktionen, die erweiterte Funktionen \(Version 1.3 der Source Control\-Plug\-in\-API\) unterstützen.  
 Diese Gruppe von Funktionen definiert, die zusätzliche Funktionalität in Version 1.3 der Source Control\-Plug\-in\-API enthalten. Sie bieten Zugriff auf Erweiterte Quellcodeverwaltungsfunktionen und Funktionen.  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Fügt eine Liste von Dateien aus Datenquellen\-Steuerelement für das aktuelle Projekt.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Ruft eine Liste der Dateien vom Datenquellen\-Steuerelement ohne Benutzeroberfläche ab.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Ruft eine Liste der Dateien im Datenquellen\-Steuerelement, die sich aus den lokalen Dateien unterscheiden.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Ruft die Flags geben an, erweiterte Funktionen, die von dem Datenquellen\-Steuerelement\-Plug\-in unterstützt.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Ruft die benutzerspezifische Optionen ab.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Überprüft eine Liste von Verzeichnissen und Dateien in einem Projekt oder in Projekten, die verwaltet werden. Jedes Verzeichnis und der Dateiname gefunden wird, eine Callback\-Funktion übergeben.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Untersucht versucht, eine Liste der Dateien ändern. Jeder Dateiname wird an eine Rückruffunktion mit dem Änderungsstatus übergeben.|  
  
## Anforderungen  
 Header: scc.h  
  
 \(Angegeben im SDK\-Umgebung gemeinsam enthält Ordner standardmäßig *\[Laufwerk\]*\\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc; auch angegeben, in dem VSIP\-Ordner mit dem MSSCCI\-Beispiel *\[Laufwerk\]*\\Program Files\\VSIP 8.0\\MSSCCI\).  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../extensibility/internals/creating-a-source-control-plug-in.md)