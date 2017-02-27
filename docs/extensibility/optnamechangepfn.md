---
title: "OPTNAMECHANGEPFN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OPTNAMECHANGEPFN"
helpviewer_keywords: 
  - "OPTNAMECHANGEPFN Callback-Funktion"
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dies ist eine Callback\-Funktion angegeben, die in einem Aufruf der [SccSetOption](../extensibility/sccsetoption-function.md) \(mit der Option `SCC_OPT_NAMECHANGEPFN`\) und wird verwendet, um Namensänderungen durch das Datenquellen\-Steuerelement\-Plug\-in wieder in die IDE zu kommunizieren.  
  
## Signatur  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)( LPVOID pvCallerData, LPCSTR pszOldName, LPCSTR pszNewName );  
```  
  
## Parameter  
 pvCallerData  
 \[in\] Benutzer Wert in einem vorherigen Aufruf der [SccSetOption](../extensibility/sccsetoption-function.md) \(mit der Option `SCC_OPT_USERDATA`\).  
  
 pszOldName  
 \[in\] Der ursprüngliche Name der Datei.  
  
 pszNewName  
 \[in\] Der Name der Datei wurde umbenannt in.  
  
## Rückgabewert  
 Keine.  
  
## Hinweise  
 Wenn während eines Datenquellen\-Steuerelement eine Datei umbenannt wird, kann das Quellcodeverwaltungs\-Plug\-in der IDE über die Änderung des Namens durch diesen Rückruf benachrichtigen.  
  
 Wenn die IDE diesem Rückruf nicht unterstützt, rufen sie nicht die [SccSetOption](../extensibility/sccsetoption-function.md) anzugeben. Wenn das plug\-in dieses Rückrufs nicht unterstützt, wird zurückgegeben, `SCC_E_OPNOTSUPPORTED` aus der `SccSetOption` funktionieren, wenn die IDE wird versucht, den Rückruf festzulegen.  
  
## Siehe auch  
 [Callback\-Funktionen, die von der IDE implementiert](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)