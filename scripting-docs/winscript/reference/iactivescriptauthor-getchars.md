---
title: 'Iactivescriptauthor:: GetChars | Microsoft-Dokumentation'
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
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576249"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Gibt den Satz von Abschluss Zeichen für einen angeforderten Vervollständigungs Kontext zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fRequestedList`  
 in Der angeforderte Vervollständigungs Kontext.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Fordert die Enumeration auf der linken Seite an.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Fordert den Element Vervollständigungs Kontext an.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003 erfordert|Fordert die Parameterliste an.|  
|SCRIPT_CMPL_COMMIT|0x0004|Fordert den Abschluss der Parameterliste an.|  
  
 `pbstrChars`  
 vorgenommen Die Zeichen, die dem angeforderten Vervollständigungs Kontext entsprechen.  
  
|`fRequestedList`-Parameter|Zurückgegebene Zeichen|  
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