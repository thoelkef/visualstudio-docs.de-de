---
title: "IActiveScriptProfilerControl3-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerControl3-Schnittstelle
Stellt eine Methode bereit, um die GC\-Heapobjekten aufzulisten, die mit einem Skriptmodul zugeordnet werden.  
  
## Syntax  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## Methoden  
 [IActiveScriptProfilerControl3::EnumHeap\-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Gibt eine Schnittstelle zurück \([IActiveScriptProfilerHeapEnum\-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) die verwendet werden kann, um die GC\-Heapobjekten im Kontext des zugeordneten Skriptmoduls zu durchlaufen.