---
title: IDebugProperty::EnumMembers | Microsoft-Dokumentation
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
ms.openlocfilehash: 527bf9d3c51dad8ffe1645dc42081dc54189ad7b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979161"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Listet die Member einer Eigenschaft.  
  
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
 [in] Gibt an, die `DBGPROP_INFO_FLAGS` Konstanten, die bestimmt, welche Felder in den Strukturen der aufgelisteten Debug-Eigenschaft ausgefüllt werden müssen.  
  
 `nRadix`  
 [in] Die Basis zum Interpretieren von numerische Informationen verwendet werden.  
  
 `refiid`  
 [in] Diese IID wird für das Filtern des Enumerators übergeben. Die IID ist eines der `IDebugPropertyEnumType` Schnittstellen, die von erben `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Gibt die `IEnumDebugPropertyInfo` -Schnittstelle, die die Elementeigenschaften zählt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType_All-Schnittstelle](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)