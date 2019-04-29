---
title: IActiveScriptAuthor::GetChars | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69cdeb16fa0791b3ff8c0cce4a4e67fe110eefc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935372"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Gibt den Satz der Abschluss Zeichen für einen Kontext für die angeforderte Abschluss.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fRequestedList`  
 [in] Der angeforderte Abschluss-Kontext.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Fordert die Links-Enumeration.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Fordert den Element-Abschluss-Kontext.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Fordert die Parameterliste.|  
|SCRIPT_CMPL_COMMIT|0x0004|Anforderungen bei Durchführung der Parameterliste.|  
  
 `pbstrChars`  
 [out] Die Zeichen, die den Kontext für die angeforderte Abschluss entsprechen.  
  
|`fRequestedList` Parameter|Zurückgegebene Zeichen|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)