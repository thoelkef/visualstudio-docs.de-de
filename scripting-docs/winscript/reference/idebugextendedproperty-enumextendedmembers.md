---
title: IDebugExtendedProperty::EnumExtendedMembers | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExtendedProperty.EnumExtendedMembers
apilocation: scrobj.dll
helpviewer_keywords: IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81b1cbb9b36d7ae237551aad2677f9480c615b88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Listet die Elemente einer erweiterten Eigenschaft an.  
  
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
 [in] Gibt an, die EX_DBGPROP_INFO_FLAGS-Konstanten, die bestimmen, dass die Felder in den aufgelisteten Debug-Eigenschaftenstruktur erweitert werden ausgefüllt werden.  
  
 `nRadix`  
 [in] Basis interpretieren alle numerischen Daten verwendet werden sollen.  
  
 `ppeepi`  
 [out] Gibt die `IEnumDebugExtendedPropertyInfo` -Schnittstelle, die die Elementeigenschaften zählt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExtendedProperty-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)