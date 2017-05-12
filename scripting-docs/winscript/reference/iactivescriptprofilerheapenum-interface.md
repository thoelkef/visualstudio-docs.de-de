---
title: "IActiveScriptProfilerHeapEnum-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum-Schnittstelle
Ein Iterator über den Heapobjekten zugeordnet mit einem Skriptmodul, durch [IActiveScriptProfilerControl3::EnumHeap\-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) erfasst.  
  
## Syntax  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## Methoden  
 [IActiveScriptProfilerHeapEnum::Next\-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Ruft das nächste Objekt oder die Objekte im Satz von Heapobjekten ab, die von [IActiveScriptProfilerControl3::EnumHeap\-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) erfasst werden.  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo\-Methode](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Ruft optionale Informationen über das angegebene Objekt im Satz von Heapobjekten ab, die von [IActiveScriptProfilerControl3::EnumHeap\-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) erfasst werden.  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo\-Methode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Gibt die angegebenen [PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md)\-Strukturen und ihre zugeordneten [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md)\-Elemente frei.  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Gibt die Zeichenfolgennamen entsprechend [PROFILER\_HEAP\_OBJECT\_NAME\_ID\-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md)\-Werten. zurück.