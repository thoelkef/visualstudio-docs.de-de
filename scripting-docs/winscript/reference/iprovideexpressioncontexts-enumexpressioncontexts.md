---
title: IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47619fface892e7e0d80141d7d4be53398a356e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Gibt einen Enumerator von ausdruckskontexten, die von dieser Komponente bezeichnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 Der Prozess-Manager verwendet diese Methode, um alle globalen ausdruckskontexten, die ein bestimmter Thread zugeordnet zu suchen.  
  
> [!NOTE]
>  Diese Methode wird vom Thread von Interesse aus aufgerufen. Es wird vom Implementierer identifizieren den aktuellen Thread und einen entsprechenden Enumerator zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IProvideExpressionContexts-Schnittstelle](../../winscript/reference/iprovideexpressioncontexts-interface.md)