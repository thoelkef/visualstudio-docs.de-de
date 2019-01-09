---
title: IDebugDocumentInfo::GetName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3ecde4fbde1a265596a01d7f0f953763363e797
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097694"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Gibt den Namen des angegebenen Dokuments zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dnt`  
 [in] Der Typ der Dokumentname zurückgegeben.  
  
 `pbstrName`  
 [out] Zeichenfolge, die mit dem Namen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Der angegebene Dokumentname ist nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den Namen des angegebenen Dokuments zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentInfo-Schnittstelle](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE-Enumeration](../../winscript/reference/documentnametype-enumeration.md)