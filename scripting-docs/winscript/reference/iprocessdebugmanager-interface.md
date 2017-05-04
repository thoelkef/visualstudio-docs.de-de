---
title: "IProcessDebugManager-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProcessDebugManager-Schnittstelle"
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager-Schnittstelle
Primäre Schnittstelle Debug ProzessManager.  Diese Schnittstelle kann eine virtuelle Anwendung von einem Prozess erstellen, hinzufügen oder entfernen.  Sie kann Stapelrahmen und Anwendungsthreads auflisten.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IProcessDebugManager`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Erstellt ein neues Debug\- Anwendungsobjekt für diese Anwendung.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Gibt ein Standard Anwendungsobjekt für den aktuellen Prozess zurück.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Fügt eine Anwendung der Computer Debug\- Liste des Managers laufender Anwendungen hinzu.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Entfernt eine Anwendung aus der Liste der laufenden Anwendung.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Erstellt ein neues debuggen Dokumentenhilfe für diese Anwendung.|