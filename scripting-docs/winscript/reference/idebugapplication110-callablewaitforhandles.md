---
title: "IDebugApplication110::CallableWaitForHandles | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::CallableWaitForHandles"
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110::CallableWaitForHandles
Wartung eines der angegebenen Handles beim Ermöglichen des den threadübergreifenden zu diesem Thread zu sendende Aufrufen signalisiert wird.  Diese Methode muss vom Debuggerthread aufgerufen werden.  
  
> [!IMPORTANT]
>  [IDebugApplication110\-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
  
```  
  
#### Parameter  
 `handleCount`  
 Die Anzahl der zu warten, den Handles.  
  
 `pHandles`  
 Der Satz warten von Handles.  
  
 `pIndex`  
 Wenn der HRESULT\-Wert S\_OK ist, der Index in `pHandles` für das Handle, das signalisiert wurde.  
  
## Siehe auch  
 [IDebugApplication110\-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md)