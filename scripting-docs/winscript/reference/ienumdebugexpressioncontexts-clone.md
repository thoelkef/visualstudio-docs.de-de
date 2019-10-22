---
title: 'Ienumdebugexpressionkontexte:: Clone | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Clone
ms.assetid: c8070ae1-120c-4b5d-bd3d-ae8fca6f9277
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70e11ec9af8859b0e1d4ecd10bd52c8c573de930
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577159"
---
# <a name="ienumdebugexpressioncontextsclone"></a>IEnumDebugExpressionContexts::Clone
Erstellt einen Enumerator, der den gleichen Zustand wie der aktuelle Enumerator enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Clone(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppedec`  
 vorgenommen Gibt die `IEnumDebugExpressionContexts`-Schnittstelle des Klons des Enumerators zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt einen Enumerator, der den gleichen Zustand wie der aktuelle Enumerator enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugExpressionContexts-Schnittstelle](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)