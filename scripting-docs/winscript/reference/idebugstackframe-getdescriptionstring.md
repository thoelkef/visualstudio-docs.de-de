---
title: 'Idebugstackframe:: getdescriptionstring | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7eb29574d240a02073721046cec65bdf483b3eb0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576745"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Gibt eine kurze oder lange Textbeschreibung des Stapel Rahmens zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fLong`  
 in Flag, bei dem `TRUE` eine lange Beschreibung zurückgibt und `FALSE` eine kurze Beschreibung zurückgibt.  
  
 `pbstrDescription`  
 vorgenommen Die Beschreibung des Stapel Rahmens.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn `fLong` `FALSE` ist, stellt diese Methode in der Regel nur den Namen der Funktion bereit, die dem Stapel Rahmen zugeordnet ist. Wenn `fLong` `TRUE` ist, kann diese Methode auch die Funktionsparameter und andere relevante Informationen bereitstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)