---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur
Stellt Informationen über optionale Heapobjekte dar.  
  
## Syntax  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO  
{  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;  
    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union  
    {  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;  
    };  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
  
```  
  
## Mitglieder  
  
|Member|Text \[Type\]|Description|  
|------------|-------------------|-----------------|  
|infoType|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE\-Enumeration](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Der Typ der optionalen Informationen.|  
|Prototyp|[PROFILER\_HEAP\_OBJECT\_ID\-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Die ID des Prototypobjekts des Heapobjekts.|  
|functionName|LPCWSTR|Der Funktionsname des Heapobjekts.|  
|elementAttributesSize|UINT|Die Größe der Heapelementattribute des Objekts.|  
|elementTextChildrenSize|UINT|Die Größe der Heaptextuntergeordneten Elementen des Objekts.|  
|scopeList|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST\-Struktur](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Die Heapbereichsliste des Objekts.|  
|internalProperty|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Die interne Eigenschaft des Heapobjekts.|  
|namePropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST\-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Eine Liste der Name\-Eigenschaft des Heapobjekts.|  
|indexPropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST\-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Eine Liste der Heapindexeigenschaften des Objekts.|  
|relationshipList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST\-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Eine Liste der Beziehungen des Heapobjekts.|  
|eventList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST\-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Eine Liste der Ereignisse des Heapobjekts.|