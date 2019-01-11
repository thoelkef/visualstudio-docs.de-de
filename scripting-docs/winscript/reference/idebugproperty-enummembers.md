---
title: IDebugProperty::EnumMembers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 7edf2d2f94519146a81cf94b3bf30946af59bbe9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097031"
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