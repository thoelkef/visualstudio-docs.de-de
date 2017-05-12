---
title: "PROFILER_HEAP_OBJECT_FLAGS-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# PROFILER_HEAP_OBJECT_FLAGS-Enumeration
Flags, die grundlegende Informationen zum Heapobjekt darstellen.  Wird in [PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md).  
  
## Syntax  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,  
    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,  
    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,  
    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,  
    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,  
    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,  
} PROFILER_HEAP_OBJECT_FLAGS;  
  
```  
  
## Mitglieder  
  
|Member|Wert|Description|  
|------------|----------|-----------------|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_NEW\_OBJECT|0x00000001|Dies Heapobjekt wurde nach die vorherige Heapenumerationsanforderung zugeordnet.  [PROFILER\_HEAP\_OBJECT\_ID\-Typ](../../winscript/reference/profiler-heap-object-id-type.md)\-Werte können wiederverwendet werden, wenn das Objekt gesammelt wird.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_IS\_ROOT|0x00000002|Dies ist ein Heapobjekt Stammobjekt des Objektdiagramms abzurufen.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SITE\_CLOSED|0x00000004|Dies Heapobjekt ist von einer Skriptsite, die geschlossen wurde.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL|0x00000008|Dies Heapobjekt wurde außerhalb des JavaScript\-GarbageCollections\-Heaps zugeordnet.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL\_UNKNOWN|0x00000010|Dies Heapobjekt wurde außerhalb Garbage Collection\-Heaps zugeordnet und IUnknown implementiert.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL\_DISPATCH|0x00000020|Dies Heapobjekt wurde außerhalb Garbage Collection\-Heaps zugeordnet und die IDISPATCH\-Schnittstelle implementiert.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SIZE\_APPROXIMATE|0x00000040|Die Größe dieses Heapobjekts ist ungefähr.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SIZE\_UNAVAILABLE|x00000080|Die Größe dieses Heapobjekts ist nicht verfügbar.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_INSTANCE|0x00000200|Das Heapobjekt ist eine Windows Runtime\-Instanz.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_RUNTIMECLASS|0x00000400|Das Heapobjekt ist eine Windows Runtime\-Ablaufklasse.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_DELEGATE|0x00000800|Das Heapobjekt ist ein Windows Runtime\-Delegat.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_NAMESPACE|0x00001000|Das Heapobjekt ist im Windows Runtime\-Namespace.|