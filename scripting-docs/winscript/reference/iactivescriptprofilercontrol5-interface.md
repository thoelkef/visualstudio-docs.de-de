---
title: "IActiveScriptProfilerControl5-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptProfilerControl5-Schnittstelle
Bietet eine Methode zur Aufzählung von GC\-Heapobjekten, die einem Skriptmodul zugeordnet sind.  
  
## Syntax  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## Methoden  
 [IActiveScriptProfilerControl5::EnumHeap2\-Methode](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Gibt eine Schnittstelle zurück \([IActiveScriptProfilerHeapEnum\-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\), die verwendet werden kann, um über die GC\-Heapobjekte im Kontext des zugeordneten Skriptmoduls zu iterieren.