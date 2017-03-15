---
title: "SccCloseProject-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCloseProject"
helpviewer_keywords: 
  - "SccCloseProject-Funktion"
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCloseProject-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion wird ein Projekt, markiert das Ende einer bestimmten Sitzung geschlossen.  
  
## Syntax  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### Parameter  
 pvContext  
 Source Control\-Plug\-in Context\-Struktur.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Das Projekt wurde erfolgreich geschlossen.|  
|SCC\_E\_PROJNOTOPEN|Es ist kein Projekt geöffnet.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Die [SccOpenProject](../extensibility/sccopenproject-function.md) wird immer aufgerufen, bevor diese Funktion. Ein Aufruf dieser Funktion folgt ein Aufruf der `SccOpenProject` Funktion oder die [SccUninitialize](../extensibility/sccuninitialize-function.md), die vollständig beendet die Verbindung mit dem Quellcodeverwaltungssystem.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)