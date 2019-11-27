---
title: 'Idebugextendedproperty:: getextendedpropertyinfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::GetExtendedPropertyInfo
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77167c46e02bcf2bf5d3ce5836ad5de103176e93
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576375"
---
# <a name="idebugextendedpropertygetextendedpropertyinfo"></a>IDebugExtendedProperty::GetExtendedPropertyInfo
Ruft erweiterte Informationen für eine erweiterte Eigenschaft ab, die mehr Informationen als die einfachere `IDebugProperty`ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFieldSpec`  
 in Gibt die EX_DBGPROP_INFO_FLAGS Konstanten an, die die in der `ExtendedDebugPropertyInfo` Struktur auszufüllenden Felder bestimmen.  
  
 `nRadix`  
 in Radix, das zum Interpretieren numerischer Informationen verwendet werden soll.  
  
 `pExtendedPropertyInfo`  
 vorgenommen Gibt die `ExtendedDebugPropertyInfo`-Struktur zurück, die die Eigenschaft beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugextendecodproperty-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)