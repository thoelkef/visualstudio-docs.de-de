---
title: "Was ist neu in Source Control-Plug-in API-Version 1.3 | Microsoft Docs"
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
  - "Quellcode-Plug-ins What's new in API-Version 1.3"
  - "Was ist der neue [Visual Studio SDK], Source Control-Plug-ins"
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Was ist neu in Source Control-Plug-in API-Version 1.3
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Version 1.3 des Quellcodeverwaltungs\-Plug\-In API bietet die folgenden neuen Funktionen eingeführt, um erweiterteres Steuerelement bereitzustellen.  
  
## Änderungen  
 Die folgenden Funktionen sind für die Version 1.3 des Quellcodeverwaltungs\-Plug\-In API neu:  
  
|Funktion|Übersicht|  
|--------------|---------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Ermöglicht die zusätzlichen Bits Funktion gemeldet werden sollen.|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Ermöglicht die Überprüfung von Dateien, die neuere Versionen in der Datenbank der Versionskontrolle vorhanden sind als auf dem lokalen Datenträger|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Lässt die Prüfung des Zustands der Namensänderungen durch Hinzufügen oder Löschen, Umbenennen \(\) angegebenen Dateien|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Ermöglicht die Überprüfung von Verzeichnissen und Dateien in der Datenbank der Versionskontrolle|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Fügt eine angegebene Liste von Dateien aus der Versionskontrolle Zieldatenbank dem aktuellen Projekt hinzu|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Führt ein automatisches „get“ aus den angegebenen Dateien aus \(keine Benutzeroberfläche angezeigt wird\)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Ermöglicht den Zugriff auf die benutzerspezifischen Optionen|  
  
## Siehe auch  
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Was ist neu in Source Control\-Plug\-in API\-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)