---
title: "Enumeratoren | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins Enumeratoren"
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Enumeratoren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Abschnitt enthält die Enumerator\-Datentypen in der Quelle Steuerelement\-Plug\-in\-API, die das Quellcodeverwaltungs\-Plug\-in zu kennen müssen.  
  
## In diesem Abschnitt  
 [Befehlscode](../extensibility/command-code-enumerator.md)  
 Listet die Optionen für die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und [SccPopulateList](../extensibility/sccpopulatelist-function.md) Funktionen.  
  
 [Nachricht](../extensibility/message-enumerator.md)  
 Listet die Flags, die für das Drucken Rückruf [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md)  
 Enthält benannte Konstante Werte, die den Status der Dateien unter Versionskontrolle angeben.  
  
 [Directory\-Statuscode](../extensibility/directory-status-code-enumerator.md)  
 Enthält benannte Konstante Werte, die den Status eines Verzeichnisses Quellcodeverwaltungsprojekt angeben.  
  
## Verwandte Abschnitte  
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definiert die Source Control\-Plug\-in SDK und beschreibt die Ressourcen enthalten.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Fordert den Benutzer um weitere Optionen für den angegebenen Befehl.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Untersucht die Liste der Dateien für den aktuellen Status an. Darüber hinaus verwendet die `pfnPopulate` Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht den Kriterien entsprechen der `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Beschreibt die Callback\-Funktion, mit der [SccOpenProject](../extensibility/sccopenproject-function.md) werden die Nachrichten vom Datenquellen\-Steuerelement\-Plug\-in in der IDE angezeigt.  
  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)  
 Enthält eine vollständige Liste aller Elemente in der Source Control\-Plug\-in\-API.