---
title: "SccPopulateDirList-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateDirList"
helpviewer_keywords: 
  - "SccPopulateDirList-Funktion"
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# SccPopulateDirList-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion bestimmt, welche Verzeichnisse und Dateien \(optional\) im Datenquellen\-Steuerelement, erhalten eine Liste von Verzeichnissen, untersuchen Sie gespeichert sind.  
  
## Syntax  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 nDirs  
 \[in\] Anzahl der Verzeichnispfade in die `lpDirPaths` Array.  
  
 lpDirPaths  
 \[in\] Array von Verzeichnispfaden untersuchen.  
  
 pfnPopulate  
 \[in\] Rückruffunktion für jedes Verzeichnispfad und \(optional\) der Dateiname im `lpDirPaths` \(siehe [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Details\).  
  
 pvCallerData  
 \[in\] Wert, der unverändert an die Rückruffunktion übergeben werden.  
  
 Bestanden  
 \[in\] Eine Kombination von Werten, die steuern, wie die Verzeichnisse verarbeitet werden \(siehe Abschnitt "PopulateDirList Flags" [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md) Mögliche Werte\).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Der Vorgang erfolgreich abgeschlossen.|  
|SCC\_E\_UNKNOWNERROR|Es ist ein Fehler aufgetreten.|  
  
## Hinweise  
 Nur die Verzeichnisse und \(optional\) Dateinamen, die tatsächlich im Quellcodeverwaltungsrepository sind, werden an die Rückruffunktion übergeben.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Fehlercodes](../extensibility/error-codes.md)