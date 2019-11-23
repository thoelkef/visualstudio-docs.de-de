---
title: 'Iactivescriptauthor:: GetEventHandler | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576231"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Gibt das Scriptlet zurück, das über die angegebenen Attribute verfügt.  
  
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
 in Das `IDispatch`-Objekt, das dem `NamedItem` entspricht, an das das Scriptlet angefügt ist.  
  
 `pszItem`  
 in Die Puffer Adresse des Bezeichner der obersten Ebene des voll qualifizierten Scriptlet-namens im Host.  
  
 `pszSubItem`  
 in Die Puffer Adresse des Bezeichners der zweiten Ebene des voll qualifizierten Scriptlet-namens im Host. Auf NULL festgelegt, wenn der Name nur eine Ebene aufweist.  
  
 `pszEvent`  
 in Die Adresse eines Puffers, der den Ereignis Namen enthält. Das Scriptlet ist ein Ereignishandler für dieses Ereignis.  
  
 `ppse`  
 vorgenommen Die Adresse einer Variablen, die einen Zeiger auf die `IScriptEntry`-Schnittstelle des Scriptlets empfängt, das über die angegebenen Attribute verfügt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptauthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)