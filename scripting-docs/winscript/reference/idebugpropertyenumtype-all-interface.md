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
ms.openlocfilehash: 737d1c5d4279a0a727f79326749dbf14a2fcd4c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574317"
---
# <a name="idebugpropertyenumtype_all-interface"></a>IDebugPropertyEnumType_All-Schnittstelle
Die `IDebugPropertyEnumType`-Schnittstellen sind so definiert, dass jede Ihrer IIDs als Filter an `IDebugProperty::EnumMembers` als Filter an übermittelt werden kann, während der entsprechende Enumerator angefordert wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Gibt eine Text Zeichenfolge zurück, die den Namen beschreibt|  
  
 Die folgenden Schnittstellen erben von `IDebugPropertyEnumType_All` und verfügen über keine zusätzlichen Methoden.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)