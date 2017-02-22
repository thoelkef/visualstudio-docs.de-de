---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaLoadCallback::NotifyDebugDir-Methode"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wird aufgerufen, wenn ein Verzeichnis Debug in der EXE\-Datei gefunden wurde.  
  
## Syntax  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### Parameter  
 `fExecutable`  
 \[in\]  `TRUE` , wenn das Verzeichnis Debug aus einer ausführbaren Datei gelesen werden \(statt einer DBG\-Datei\).  
  
 `cbData`  
 \[in\]  Anzahl von Datenbytes Verzeichnis Debug.  
  
 `data[]`  
 \[in\]  Ein Array, das dem Verzeichnis Debug ausgefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Der Rückgabecode wird meist ignoriert.  
  
## Hinweise  
 Die [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode ruft diesen Rückruf auf, wenn ein Verzeichnis Debug beim Verarbeiten der ausführbaren Datei gesucht wird.  
  
 Diese Methode entfernt die Anforderung für den Client an den Reverse Engineering die ausführbare Datei und\/oder die Datei Debuggen starten, um Debuginformationen zu unterstützen, die in der PDB\-Datei.  Mit diesem können Daten, der Client den Typ von Debuginformationen verfügbar erkennen und ob er in der ausführbaren Datei oder einer DBG\-Datei befindet.  
  
 Die meisten Clients diesen Rückruf nicht benötigt, da die `IDiaDataSource::loadDataForExe`\-Methode transparent .pdb .dbg\-Dateien und bei Bedarf geöffnet wird, um Symbole zu dienen.  
  
## Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)