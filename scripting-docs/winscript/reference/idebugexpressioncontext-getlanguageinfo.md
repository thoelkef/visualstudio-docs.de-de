---
title: 'Idebugexpressioncontext:: getlanguageinfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.GetLanguageInfo
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::GetLanguageInfo
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e6dd3d3bb254cd91f411da3b6b587bc37c3a777
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576411"
---
# <a name="idebugexpressioncontextgetlanguageinfo"></a>IDebugExpressionContext::GetLanguageInfo
Gibt einen Namen und eine GUID für die Sprache zurück, die diesen Kontext besitzt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrLanguageName`  
 vorgenommen Der Name der Sprache.  
  
 `pLanguageID`  
 vorgenommen Die eindeutige ID für die Sprache.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt einen Namen und eine GUID für die Sprache zurück, die diesen Kontext besitzt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionContext-Schnittstelle](../../winscript/reference/idebugexpressioncontext-interface.md)