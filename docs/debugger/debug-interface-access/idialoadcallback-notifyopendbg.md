---
title: "IDiaLoadCallback::NotifyOpenDBG | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyOpenDBG-Methode"
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::NotifyOpenDBG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wird aufgerufen, wenn eine mögliche dbg\-datei geöffnet wurde.  
  
## Syntax  
  
```cpp#  
HRESULT NotifyOpenDBG (   
   LPCOLESTR dbgPath,  
   HRESULT   resultCode  
);  
```  
  
#### Parameter  
 `dbgPath`  
 \[in\]  Der vollständige Pfad der DBG\-Datei.  
  
 `resultCode`  
 \[in\]  Code, der`S_OK`\(Erfolg\) oder Misserfolg des Ladevorgangs in Bezug auf diese Datei angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Der Rückgabecode wird meist ignoriert.  
  
## Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)