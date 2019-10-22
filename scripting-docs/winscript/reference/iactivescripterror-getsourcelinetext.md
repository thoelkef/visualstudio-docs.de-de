---
title: 'Iactivescripterror:: getsourcelinetext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourceLineText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ded57f97ec40167bac34bf0f288c2e3d15a5c4b7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576916"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
Ruft die Zeile in der Quelldatei ab, in der ein Fehler aufgetreten ist, während eine Skript-Engine ein Skript ausgeführt hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>Parameter  
 `pbstrSourceLine`  
 vorgenommen Adresse eines Puffers, der die Zeile des Quellcodes empfängt, in der der Fehler aufgetreten ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_FAIL`, wenn die Zeile in der Quelldatei nicht abgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)