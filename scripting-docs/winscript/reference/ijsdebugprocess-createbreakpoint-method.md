---
title: "IJsDebugProcess::CreateBreakPoint-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess::CreateBreakPoint-Methode
Legt den Haltepunkt an der angegebenen Dokumentposition fest.  
  
## Syntax  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### Parameter  
 `documentId`  
 \[in\] Zeiger auf "IDebugDocumentText".  
  
 `characterOffset`  
 \[in\] Zeichenoffset vom Anfang der Datei.  
  
 `characterCount`  
 \[in\] Länge des Dokumenttexts, in den der Haltepunkt eingefügt werden soll.  
  
 `isEnabled`  
 \[in\] Gibt an, ob der Haltepunkt aktiviert ist.  
  
 `ppDebugBreakPoint`  
 \[out\] Objekt, das den Haltepunkt darstellt, der erstellt wurde.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugProcess\-Schnittstelle](../../winscript/reference/ijsdebugprocess-interface.md)