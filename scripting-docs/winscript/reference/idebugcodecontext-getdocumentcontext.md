---
title: IDebugCodeContext::GetDocumentContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: IDebugCodeContext::GetDocumentContext
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 098d57a5ff0ba14b1dd493ad772eee595a10ec9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcodecontextgetdocumentcontext"></a>IDebugCodeContext::GetDocumentContext
Gibt den Dokumentenkontext dieses Codekontext zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppsc`  
 [out] Der Dokumentenkontext dieses Codekontext zugeordnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Textdokumente sollte die Zeichenposition Bereich den Text für die gesamte Anweisung enthalten sein. Dadurch kann der Debugger IDE zum Markieren der aktuellen quellanweisung.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCodeContext-Schnittstelle](../../winscript/reference/idebugcodecontext-interface.md)