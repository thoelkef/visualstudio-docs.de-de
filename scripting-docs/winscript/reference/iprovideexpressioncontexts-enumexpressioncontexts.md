---
title: IProvideExpressionContexts::EnumExpressionContexts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1e4c462780f7026329ff7a5d22c86dbb6058dc5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157749"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Gibt einen Enumerator von ausdruckskontexten, die von dieser Komponente bezeichnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppedec`  
 [out] Ein Enumerator von ausdruckskontexten, die von dieser Komponente bezeichnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Prozessbasierten Debug-Manager verwendet diese Methode, um alle globalen ausdruckskontexten, die einem bestimmten Thread suchen.  
  
> [!NOTE]
>  Diese Methode wird der Thread von Interesse aus aufgerufen. Es obliegt dem Implementierer, identifizieren den aktuellen Thread und einen entsprechenden Enumerator zurückgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IProvideExpressionContexts-Schnittstelle](../../winscript/reference/iprovideexpressioncontexts-interface.md)