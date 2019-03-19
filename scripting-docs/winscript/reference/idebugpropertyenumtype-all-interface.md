---
title: IDebugPropertyEnumType_All-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ddd9fb24aa83a6027d6d705de6a748a96b2e28
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149294"
---
# <a name="idebugpropertyenumtypeall-interface"></a>IDebugPropertyEnumType_All-Schnittstelle
Die `IDebugPropertyEnumType` Schnittstellen definiert wurden, sodass jeder, der die IIDs als Filter, um übergeben werden kann `IDebugProperty::EnumMembers` beim Anfordern des entsprechenden Enumerators.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Gibt eine Zeichenfolge, die den Namen beschreibt.|  
  
 Die folgenden Schnittstellen erben `IDebugPropertyEnumType_All`, und verfügen über keine zusätzlichen Methoden.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)