---
title: "Anwendung der Einstellungen f&#252;r mehrere Project-Verbindungen | Microsoft Docs"
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
  - "Source Control Plug-ins und Anwendung von Einstellungen"
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Anwendung der Einstellungen f&#252;r mehrere Project-Verbindungen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Quellcodeverwaltungs\-Plug\-In, mit dem das Quellcodeverwaltungs\-Plug\-In API 1.2 erstellt wurde, kann einen Batchvorgang verwendet werden, um denselben Quellcodeverwaltungsvorgang auf mehrere Projekte oder mehrere kontexten Verbindung auszuführen.  Batches können verwendet werden, um redundanten, Dialogfelder pro Projekt aus der Benutzerfreundlichkeit zu beseitigen.  
  
 Wenn ein Benutzer mehrere Elemente auswählen, die mehr als einer Verbindung in einem Quellcodeverwaltungs\-Plug\-In gehören, mit dem das Quellcodeverwaltungs\-Plug\-In API 1.1 erstellt wurde \(z. B. zwei Webprojekte auf verschiedenen Dateifreigabe computern\) und auschecken, sieht der Benutzer das gleiche Dialogfeld wiederholt.  Dies geschieht, auch wenn der Benutzer auf das Kontrollkästchen klickt im Dialogfeld **Auf alle anwenden** , da die IDE den Zustand für jeden Kontext Verbindung zurücksetzt.  
  
## Ein neues Funktions\-Flag  
 `SccBeginBatch`\-Funktion `SCC_CAP_BATCH` legt das Flag fest, um anzugeben, dass ein Batchvorgang noch ausgeführt wird  
  
## Neue Funktionen  
 Die folgenden neuen Features unterstützen den Batchvorgang:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 Die `SCCBeginBatch`\-Funktion startet eine Gruppe Quellcodeverwaltungsvorgänge.  `SccEndBatch` die Gruppe gehören.  Die Gruppen werden nicht geschachtelt werden.  
  
## Siehe auch  
 [Was ist neu in Source Control\-Plug\-in API\-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)