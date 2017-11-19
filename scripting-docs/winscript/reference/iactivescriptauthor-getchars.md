---
title: IActiveScriptAuthor::GetChars | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abc9c819c2dd4a75d6223af86b4fe89baebc186b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Gibt den Satz der Abschluss Zeichen für einen Kontext für die angeforderte Abschluss.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|SCRIPT_CMPL_ENUM_TRIGGER|0 x 0001|Fordert an die linken Seite-Enumeration.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0 x 0002|Fordert den Member-Abschluss-Kontext.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0 x 0003|Fordert die Parameterliste.|  
|SCRIPT_CMPL_COMMIT|0 x 0004|Fordert den Abschluss der Parameterliste.|  
  
 `pbstrChars`  
 [out] Die Zeichen, die auf den Abschluss des angeforderten Vorgangs Kontext entsprechen.  
  
|`fRequestedList`Parameter|Zurückgegebene Zeichen|  
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