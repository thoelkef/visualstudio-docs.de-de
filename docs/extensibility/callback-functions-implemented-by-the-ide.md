---
title: "Callback-Funktionen, die von der IDE implementiert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins Rückruffunktionen"
  - "Rückruffunktionen Source Control-Plug-ins"
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Callback-Funktionen, die von der IDE implementiert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Integration mit stellen kann der integrated Development Environment \(IDE\) als nahtlos wie möglich und eine einheitliche benutzererfahrung das Quellcodeverwaltungs\-Plug\-in Rückruffunktionen verwenden, die von der IDE implementiert werden. Das plug\-in kann diese Funktionen zum entsprechenden Zeitpunkt während eines Datenquellen\-Steuerelement übergeben von Informationen an die IDE aufrufen. die IDE können Sie diese Informationen als eingebettete Elemente in die systemeigene Benutzeroberfläche anzeigen. Der Benutzer hat eine weniger fragmentierte Erfahrung in diesem Szenario als wenn das plug\-in eine eigene Benutzeroberfläche beschäftigt.  
  
 Die erforderlichen Header\-Datei ist scc.h. Der Standardspeicherort ist \\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc\\. Sie ist auch in den VSIP\-Ordner mit dem Datenquellen\-Steuerelement\-Plug\-in Beispiel am \\Program Files\\VSIP 8.0\\MSSCCI\\.  
  
## In diesem Abschnitt  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Beschreibt die Callback\-Funktion, mit der [SccOpenProject](../extensibility/sccopenproject-function.md) werden die Nachrichten vom Datenquellen\-Steuerelement\-Plug\-in in der IDE angezeigt.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Beschreibt die Callback\-Funktion, mit der [SccPopulateList](../extensibility/sccpopulatelist-function.md) bei die IDE keinen vollständigen Zugriff auf Informationen, die nur für das Quellcodeverwaltungs\-Plug\-in, z. B. eine vollständige Liste der Dateien unter Versionskontrolle verfügbar sind.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Beschreibt die Callback\-Funktion, mit der die [SccQueryChanges](../extensibility/sccquerychanges-function.md) Vorgang.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Beschreibt die Callback\-Funktion, mit der die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Vorgang.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Beschreibt die Callback\-Funktion festlegen, indem Sie einen Aufruf der [SccSetOption](../extensibility/sccsetoption-function.md) die das Datenquellen\-Steuerelement kommunizieren Namensänderungen zurück, in der IDE\-Plug\-in ermöglicht.  
  
## Verwandte Abschnitte  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Öffnet ein Projekt.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Untersucht die Liste der Dateien für den aktuellen Status an. Darüber hinaus verwendet die `pfnPopulate` Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht den Kriterien entsprechen der `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Überprüft eine Liste von Verzeichnissen und Dateien in einem Projekt oder in Projekten, die verwaltet werden. Jedes Verzeichnis und der Dateiname gefunden wird, eine Callback\-Funktion übergeben.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Überprüft die Änderungen, die eine Liste der Dateien vorgenommen wurden. Jeder Dateiname wird an eine Callback\-Funktion zusammen mit seinem Änderungsstatus übergeben.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Legt eine Vielzahl von Optionen fest. Jede Option beginnt mit `SCC_OPT_xxx` und verfügt über einen eigenen definierten Satz von Werten.  
  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)  
 Beschreibt den Inhalt des Abschnitts Verweis Source Control\-Plug\-in\-SDK.