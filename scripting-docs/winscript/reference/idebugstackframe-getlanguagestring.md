---
title: 'Idebugstackframe:: getlanguagestring | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83abb038cd8bc018d84cd0c5ddd2a413f8a02248
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576758"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Gibt eine kurze oder lange Textbeschreibung der Sprache zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fLong`  
 in Flag, bei dem `TRUE` eine lange Beschreibung zurückgibt und `FALSE` eine kurze Beschreibung zurückgibt.  
  
 `pbstrLanguage`  
 vorgenommen Die Beschreibung der Sprache.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn `fLong` `FALSE` ist, stellt diese Methode in der Regel nur den Namen der Sprache bereit, die dem Stapel Rahmen zugeordnet ist. Wenn `fLong` `TRUE` ist, kann diese Methode eine vollständige Produktbeschreibung bereitstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)