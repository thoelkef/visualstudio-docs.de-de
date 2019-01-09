---
title: IDebugStackFrame::GetDescriptionString | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f6479485a508f71797d6965f71edd3253927088
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097226"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Gibt eine kurze oder lange Text Beschreibung des Stapelrahmens zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fLong`  
 [in] Flag, in denen `TRUE` gibt eine lange Beschreibung und `FALSE` gibt eine kurze Beschreibung zurück.  
  
 `pbstrDescription`  
 [out] Die Beschreibung des Stapelrahmens.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 In der Regel, wenn `fLong` ist `FALSE`, diese Methode bietet nur den Namen der Funktion, die dem Stapelrahmen zugeordnet. Wenn `fLong` ist `TRUE`, diese Methode kann auch bereitstellen, die Funktionsparameter und weitere relevante Informationen ein.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)