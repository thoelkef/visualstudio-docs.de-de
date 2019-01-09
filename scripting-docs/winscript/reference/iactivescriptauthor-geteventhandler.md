---
title: IActiveScriptAuthor::GetEventHandler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e7f6cc265815db4acd847270b28c3e744257fa0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086683"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Gibt zurück, das Scriptlet, das die angegebenen Attribute aufweist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdisp`  
 [in] Die `IDispatch` Objekt, das entspricht, dem `NamedItem` , dem das Scriptlet zugeordnet ist.  
  
 `pszItem`  
 [in] Die Pufferadresse des Bezeichners der obersten Ebene mit dem vollständig qualifizierten Scriptlet-Namen auf dem Host.  
  
 `pszSubItem`  
 [in] Die Pufferadresse der Bezeichner der zweiten Ebene mit dem vollständig qualifizierten Scriptlet-Namen auf dem Host. Auf NULL festgelegt, wenn der Name nur eine Ebene enthält.  
  
 `pszEvent`  
 [in] Die Adresse eines Puffers, der den Namen des Ereignisses enthält. Das Scriptlet ist ein Handler für dieses Ereignis.  
  
 `ppse`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptEntry` Schnittstelle des Scriptlets, die die angegebenen Attribute aufweist.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)