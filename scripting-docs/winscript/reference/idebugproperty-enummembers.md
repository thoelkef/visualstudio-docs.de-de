---
title: 'Idebugproperty:: EnumMembers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562420"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Listet die Member einer Eigenschaft auf.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFieldSpec`  
 in Gibt die `DBGPROP_INFO_FLAGS` Konstanten an, die bestimmen, welche Felder in den aufgelisteten Debug-Eigenschafts Strukturen ausgefüllt werden sollen.  
  
 `nRadix`  
 in Radix, das zum Interpretieren numerischer Informationen verwendet werden soll.  
  
 `refiid`  
 in Diese IID wird zum Filtern des Enumerators übermittelt. Die IID ist eine der `IDebugPropertyEnumType` Schnittstellen, die von `IDebugPropertyEnumType_All` erben.  
  
 `ppEnum`  
 vorgenommen Gibt die `IEnumDebugPropertyInfo`-Schnittstelle zurück, die die Element Eigenschaften auflistet.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugproperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 [IDebugPropertyEnumType_All-Schnittstelle](../../winscript/reference/idebugpropertyenumtype-all-interface.md)    
 [IEnumDebugPropertyInfo-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)