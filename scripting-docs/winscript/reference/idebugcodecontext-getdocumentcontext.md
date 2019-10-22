---
title: 'Idebugcodecontext:: getdocumentcontext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.GetDocumentContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::GetDocumentContext
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dc1cda6164375f3434ee562b540e85268fe4c68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573223"
---
# <a name="idebugcodecontextgetdocumentcontext"></a>IDebugCodeContext::GetDocumentContext
Gibt den Dokument Kontext zurück, der diesem Code Kontext zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppsc`  
 vorgenommen Der Dokument Kontext, der diesem Code Kontext zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Bei Textdokumenten sollte der Zeichen Positions Bereich den Text für die gesamte-Anweisung enthalten. Dies ermöglicht der Debugger-IDE, die aktuelle Quell Anweisung hervorzuheben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCodeContext-Schnittstelle](../../winscript/reference/idebugcodecontext-interface.md)