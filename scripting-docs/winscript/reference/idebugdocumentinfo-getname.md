---
title: 'Idebugdocumentinfo:: GetName | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570955"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Gibt den angegebenen Dokumentnamen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dnt`  
 in Der Typ des Dokument namens, der zurückgegeben werden soll.  
  
 `pbstrName`  
 vorgenommen Zeichenfolge, die den Namen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Der angegebene Dokument Name ist nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den angegebenen Dokumentnamen zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumentinfo-Schnittstelle](../../winscript/reference/idebugdocumentinfo-interface.md)    
 [DOCUMENTNAMETYPE-Enumeration](../../winscript/reference/documentnametype-enumeration.md)