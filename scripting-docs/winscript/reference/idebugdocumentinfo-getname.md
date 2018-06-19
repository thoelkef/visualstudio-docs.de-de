---
title: IDebugDocumentInfo::GetName | Microsoft Docs
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
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726590"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Gibt den Namen des angegebenen Dokuments zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dnt`  
 [in] Der Typ des zurückzugebenden Dokumentnamen.  
  
 `pbstrName`  
 [out] Die Zeichenfolge mit dem Namen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Den Namen des angegebenen Dokuments ist nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den Namen des angegebenen Dokuments zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentInfo-Schnittstelle](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE-Enumeration](../../winscript/reference/documentnametype-enumeration.md)