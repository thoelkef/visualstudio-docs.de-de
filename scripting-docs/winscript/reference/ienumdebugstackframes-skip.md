---
title: IEnumDebugStackFrames::Skip | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugStackFrames.Skip
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugStackFrames::Skip
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79267220c7ad3ce19d1901c6371554c7aabacde8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugstackframesskip"></a>IEnumDebugStackFrames::Skip
Überspringt eine angegebene Anzahl von Segmenten in einem Enumerationsfolge an.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der Segmente in der Enumeration Sequenz zu überspringen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode lässt es sich um eine angegebene Anzahl von Segmenten in einem Enumerationsfolge.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugStackFrames-Schnittstelle](../../winscript/reference/ienumdebugstackframes-interface.md)