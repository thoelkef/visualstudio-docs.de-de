---
title: 'Idebugextendecodproperty:: enumextenenddmembers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6fd225be9504254965eab77b912f50fb5c777e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576392"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Listet die Member einer erweiterten Eigenschaft auf.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFieldSpec`  
 in Gibt die EX_DBGPROP_INFO_FLAGS Konstanten an, die die Felder in den aufgelisteten erweiterten Debug-Eigenschafts Strukturen bestimmen, die ausgefüllt werden sollen.  
  
 `nRadix`  
 in Radix, das zum Interpretieren numerischer Informationen verwendet werden soll.  
  
 `ppeepi`  
 vorgenommen Gibt die `IEnumDebugExtendedPropertyInfo`-Schnittstelle zurück, die die Element Eigenschaften auflistet.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugextendecodproperty-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)