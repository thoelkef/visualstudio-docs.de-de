---
title: IDebugExtendedProperty::EnumExtendedMembers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 400145cf3981b7266a796f66576eb12f979d2750
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949837"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Listet die Member einer erweiterten Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFieldSpec`  
 [in] Gibt an, dass die EX_DBGPROP_INFO_FLAGS-Konstanten, die bestimmen, dass die Felder in den aufgelisteten Strukturen der Debug-Eigenschaft, die erweitert werden, gefüllt werden soll.  
  
 `nRadix`  
 [in] Die Basis zum Interpretieren von numerische Informationen verwendet werden.  
  
 `ppeepi`  
 [out] Gibt die `IEnumDebugExtendedPropertyInfo` -Schnittstelle, die die Elementeigenschaften zählt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExtendedProperty-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)