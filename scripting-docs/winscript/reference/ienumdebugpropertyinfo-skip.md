---
title: IEnumDebugPropertyInfo::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d0f8ff65340edfac1c02e5b7e80b7be3fd257c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727210"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Überspringt die angegebene Anzahl von `DebugPropertyInfo` Strukturen in eine Enumerationsfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der `DebugPropertyInfo` Strukturen in der Enumeration Sequenz zu überspringen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`, in der Regel `S_OK`. Gibt `S_FALSE` und legt den aktuellen Elementzeiger bis zum Ende der Enumeration fest, wenn `celt` ist größer als die Anzahl von Elementen nach links im Enumerator.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugPropertyInfo-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)