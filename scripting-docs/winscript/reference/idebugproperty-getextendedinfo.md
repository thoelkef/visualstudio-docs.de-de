---
title: 'Idebugproperty:: getextendecodinfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562392"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Ruft erweiterte Informationen für die-Eigenschaft ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cInfos`  
 in Anzahl der erweiterten Informationsobjekte.  
  
 `rgguidExtendedInfo`  
 in Ein Array von `GUID`s wird übermittelt, sodass mehrere Elemente erweiterter Informationen gleichzeitig abgerufen werden können.  
  
 `pExtendedInfo`  
 vorgenommen Gibt ein Array von `VARIANT`s zurück, das zum Abrufen der erweiterten Eigenschaften Informationen verwendet werden kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ruft erweiterte Informationen für dieses Objekt ab. Die API ist nur zum Abrufen von Informationen vorhanden, die sich nicht für das Abrufen durch `IDebugProperty::GetPropertyInfo`) eignen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)