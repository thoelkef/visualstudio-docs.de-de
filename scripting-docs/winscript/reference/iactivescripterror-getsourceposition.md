---
title: 'Iactivescripterror:: getsourceposition | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 76ed307f988a3e5bf77ff978c466eda6e5dfee18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576882"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Ruft den Speicherort im Quellcode ab, an dem ein Fehler aufgetreten ist, während die Skript-Engine ein Skript ausgeführt hat.  
  
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
 vorgenommen Adresse einer Variablen, die ein Cookie empfängt, das den Kontext identifiziert. Die Interpretation dieses Parameters hängt von der Host Anwendung ab.  
  
 `pulLineNumber`  
 vorgenommen Adresse einer Variablen, die die Zeilennummer in der Quelldatei empfängt, in der der Fehler aufgetreten ist.  
  
 `pichCharPosition`  
 vorgenommen Adresse einer Variablen, die die Zeichenposition in der Zeile empfängt, in der der Fehler aufgetreten ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_FAIL`, wenn der Speicherort nicht abgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)