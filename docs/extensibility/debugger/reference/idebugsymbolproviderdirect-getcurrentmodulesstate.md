---
title: "IDebugSymbolProviderDirect::GetCurrentModulesState | Microsoft Docs"
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
  - "GetCurrentModulesState"
  - "IDebugSymbolProviderDirect::GetCurrentModulesState"
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect::GetCurrentModulesState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft Informationen zu der Gruppe Symbol ab, aus der der Symbol für Mitglied ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetCurrentModulesState(  
    DWORD*          pState,  
    unsigned long * count  
);  
```  
  
```c#  
int GetCurrentModulesState(  
    out uint pState,  
    out uint count  
);  
```  
  
#### Parameter  
 `pState`  
 \[out\]  Der Zustand der Gruppe Anbieter Symbol.  
  
 `count`  
 \[out\]  Die Anzahl der Module in der Gruppe.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Zustand wird, wenn ein Modul hinzugefügt oder aus der Gruppe entfernt Symbol geändert.  Deshalb kann diese Methode verwendet werden, um zu ermitteln, ob eine Gruppe von Symbolen geändert wurde.  
  
## Siehe auch  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)