---
title: IDebugPropertyEnumType_All-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugPropertyEnumType_All
apilocation: scrobj.dll
helpviewer_keywords: IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75de35bd42ea91e7d27523ba42c392650686041a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenumtypeall-interface"></a>IDebugPropertyEnumType_All-Schnittstelle
Die `IDebugPropertyEnumType` Schnittstellen definiert wurden, sodass alle ihre IIDs als Filter, um übergeben werden kann `IDebugProperty::EnumMembers` beim Anfordern von des entsprechenden Enumerators.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Gibt eine Textzeichenfolge, die den Namen beschreibt.|  
  
 Die folgenden Schnittstellen erben `IDebugPropertyEnumType_All`, und Sie verfügen über keine zusätzlichen Methoden.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)