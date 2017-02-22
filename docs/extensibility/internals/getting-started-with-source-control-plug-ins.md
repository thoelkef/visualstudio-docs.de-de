---
title: "Erste Schritte mit Source Control-Plug-ins | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins, erste Schritte"
  - "Erste Schritte, Quelle Steuerelement-Plug-ins"
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Erste Schritte mit Source Control-Plug-ins
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Um ein Quellcodeverwaltungs\-Plug\-In zu erstellen, müssen Sie eine DLL erstellen, das die Funktionen implementiert, die im Quellcodeverwaltungs\-Plug\-In APIs definiert sind, und registrieren Sie dann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit der DLL bereitzustellen, um sie für die Verwendung in der Quellcode versionskontrolle.  
  
 Drei Versionen des Quellcodeverwaltungs\-Plug\-In API \(Versionen 1.1, 1.2 und 1.3\) sind für steckverbindungen Quellcodeverwaltung verfügbar.  Das Quellcodeverwaltungs\-Plug\-In API, die hier dokumentiert wird, ist Version 1.3.  Sie wurde entworfen, um mit den steckverbindungen Quellcodeverwaltung vollständig kompatibel zu sein, die den Versionen 1.1 und 1.2 unterstützen.  Die [Was ist neu in Source Control\-Plug\-in API\-Version 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)\-Abschnitt angezeigt, welche die neuen Funktionen in die aktuelle Version des Quellcodeverwaltungs\-Plug\-In APIs unterstützen.  
  
## In diesem Abschnitt  
 [Gewusst wie: Installieren Sie ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Beschreibt, wie die Registrierungseinträge macht, die dem Plug\-In ein Quellcodeverwaltung DLL erforderlich sind.  
  
 [Was ist neu in Source Control\-Plug\-in API\-Version 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Bietet eine kurze Übersicht über die Änderungen bereit, die für das Quellcodeverwaltungs\-Plug\-In APIs in Version 1.3 vorgenommen wurden.  
  
 [Was ist neu in Source Control\-Plug\-in API\-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Bietet eine kurze Übersicht über die Änderungen bereit, die für das Quellcodeverwaltungs\-Plug\-In APIs in Version 1.2 vorgenommen wurden.  
  
## Verwandte Abschnitte  
 [Source Control\-Plug\-ins](../../extensibility/source-control-plug-ins.md)  
 Stellt vollständige Liste aller Elemente im Quellcodeverwaltungs\-Plug\-In API bereit.  
  
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definiert das Quellcodeverwaltungs\-Plug\-In SDK, und beschreibt die enthaltenen Ressourcen frei.