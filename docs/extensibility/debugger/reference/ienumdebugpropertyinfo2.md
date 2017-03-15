---
title: "IEnumDebugPropertyInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2"
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle listet [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen auf.  
  
## Syntax  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um Informationen für eine bestimmte Eigenschaft darstellt.  
  
## Hinweise für Aufrufer  
 Rufen Sie [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) an, die zum Abrufen dieser Schnittstelle, die die untergeordneten Elemente einer bestimmten Eigenschaft darstellt.  Rufen Sie [\[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) an, die zum Abrufen dieser Schnittstelle, die die Eigenschaften eines bestimmten Stapelrahmens darstellt.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugPropertyInfo2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Ruft eine angegebene Anzahl [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Überspringt eine angegebene Anzahl [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in der Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Ruft die Anzahl der [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einem Enumerator ab.|  
  
## Hinweise  
 Grundsätzlich handelt es sich um eine Eigenschaft einer Hierarchie von Informationen, die einen Namen, einen Wert, eine Adresse und einen Typ enthalten kann, sowie von allen weiteren Informationen, die zum zugeordneten Eigenschaftenobjekt oder Stapelrahmen äquivalent sind.  Ausführliche Informationen finden Sie unter [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md).  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [\[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)