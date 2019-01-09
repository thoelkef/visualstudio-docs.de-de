---
title: IActiveScriptError::GetSourcePosition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb5adfe508b7b5d3de0cf7f508d8c801a36adf1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097369"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Ruft die Position im Quellcode, in denen ist ein Fehler aufgetreten, während die Skript-Engine ein Skript ausgeführt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwSourceContext`  
 [out] Die Adresse einer Variablen, die einen Cookie empfängt, der den Kontext angibt. Die Interpretation dieses Parameters hängt von der hostanwendung ab.  
  
 `pulLineNumber`  
 [out] Die Adresse einer Variablen, die die Nummer der Zeile in der Quelldatei erhält, in dem der Fehler aufgetreten ist.  
  
 `pichCharPosition`  
 [out] Die Adresse einer Variablen, die die Zeichenposition in der Zeile empfängt, in dem der Fehler aufgetreten ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` , wenn der Speicherort nicht abgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)