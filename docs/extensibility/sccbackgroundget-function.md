---
title: "SccBackgroundGet-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccBackgroundGet"
helpviewer_keywords: 
  - "SccBackgroundGet-Funktion"
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccBackgroundGet-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft aus der quellcodeverwaltung jede der angegebenen Dateien ohne Benutzereingriff.  
  
## Syntax  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 nFiles  
 \[in\] Anzahl der angegebenen Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 \[in, out\] Array der Namen der Dateien abgerufen werden sollen.  
  
> [!NOTE]
>  Die Namen müssen vollqualifizierte Namen lokaler Dateien sein.  
  
 dwFlags  
 \[in\] Befehl Flags \(`SCC_GET_ALL`, `SCC_GET_RECURSIVE`\).  
  
 dwBackgroundOperationID  
 \[in\] Ein eindeutiger Wert, der diesen Vorgang zugeordnet ist.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Der Vorgang wurde erfolgreich abgeschlossen.|  
|SCC\_E\_BACKGROUNDGETINPROGRESS|Hintergrund\-Abruf wird bereits ausgeführt \(das Quellcodeverwaltungs\-Plug\-in sollte dies nur zurück, wenn es keine anderen Batch\-Vorgänge unterstützt\).|  
|SCC\_I\_OPERATIONCANCELED|Vorgang wurde abgebrochen, bevor Sie abgeschlossen wird.|  
  
## Hinweise  
 Diese Funktion wird immer in einem anderen Thread aufgerufen, die das Quellcodeverwaltungs\-Plug\-In geladen. Diese Funktion wird nicht erwartet zurückgegeben, bis es fertig ist. Allerdings kann es mehrere Male mit mehreren Listen von Dateien zur gleichen Zeit aufgerufen werden.  
  
 Die Verwendung der `dwFlags` Argument ist identisch mit der [SccGet](../extensibility/sccget-function.md).  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)