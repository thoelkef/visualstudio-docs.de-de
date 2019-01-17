---
title: IActiveScriptProfilerHeapEnum-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14562654e0fd3f3567d6f598f84cf2c966b1b8cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344888"
---
# <a name="iactivescriptprofilerheapenum-interface"></a>IActiveScriptProfilerHeapEnum-Schnittstelle
Ein Iterator für den Heap Objekten zugeordneten eine Skript-Engine, die gesammelt werden, indem die [iactivescriptprofilercontrol3:: Enumheap-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Syntax  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>Methoden  
 [IActiveScriptProfilerHeapEnum::Next-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Ruft das nächste Objekt oder Objekte in der Menge der Heap-Objekte, die gesammelt werden, indem die [iactivescriptprofilercontrol3:: Enumheap-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo-Methode](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Ruft optionale Informationen für das angegebene Objekt in der Menge der Heap-Objekte, die gesammelt werden, indem die [iactivescriptprofilercontrol3:: Enumheap-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo-Methode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Gibt das angegebene frei [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md) Strukturen und ihre zugeordneten [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) Elemente.  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Gibt die Zeichenfolgennamen für [PROFILER_HEAP_OBJECT_NAME_ID-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md) Werte...