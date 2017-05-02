---
title: "IDebugPropertyEnumType_All-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugPropertyEnumType_All-Schnittstelle"
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPropertyEnumType_All-Schnittstelle
Die `IDebugPropertyEnumType`\-Schnittstellen werden definiert, sodass jedes ihres IID als Filter auf `IDebugProperty::EnumMembers` beim Anfordern des entsprechenden Enumerators übergeben werden kann.  
  
## Syntax  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugPropertyEnumType\_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Gibt eine Zeichenfolge zurück, die den Namen beschreibt|  
  
 Die folgenden Schnittstellen erben von `IDebugPropertyEnumType_All` und haben keine zusätzlichen Methoden.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## Siehe auch  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)