---
title: 'Idebugproperty:: GetPropertyInfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0698e09cd9643322a237a81d971248577fd97e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562327"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Ruft den Wert eines `IDebugProperty` ab, der eine Methode oder eine indizierte Eigenschaft beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 in Gibt die `DBGPROP_INFO_FLAGS` Konstanten an, die die in der `DebugPropertyInfo` Struktur auszufüllenden Felder bestimmen.  
  
 `nRadix`  
 in Radix, das beim Formatieren numerischer Informationen verwendet werden soll.  
  
 `pPropertyInfo`  
 vorgenommen Gibt die `DebugPropertyInfo`-Struktur zurück, die die Eigenschaft beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugproperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)