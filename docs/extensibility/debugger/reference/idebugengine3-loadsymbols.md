---
title: "IDebugEngine3::LoadSymbols | Microsoft Docs"
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
  - "IDebugEngine3::LoadSymbols"
helpviewer_keywords: 
  - "IDebugEngine3::LoadSymbols"
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Lädt \(falls erforderlich\) Symbole für alle Module, die für dieses Modul Debuggen gedebuggt werden.  
  
## Syntax  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```c#  
int LoadSymbols();  
```  
  
#### Parameter  
 Keine.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 Dadurch lädt Debugsymbole für alle Module, die für dieses Modul Debuggen verwiesen werden.  Die Symbole werden nur geladen, wenn sie noch nicht geladen wurden.  Symbole werden in den Verzeichnissen durchsucht, die durch einen Aufruf von [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)festgelegt werden.  
  
## Siehe auch  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)