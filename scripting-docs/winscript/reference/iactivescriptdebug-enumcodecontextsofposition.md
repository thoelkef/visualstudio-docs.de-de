---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40fd8e2d19d3949ff26811956ae3d203871e5510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645590"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Ein Smarthost, die zum Delegieren der `IDebugDocumentContext::EnumCodeContexts` Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSourceContext`  
 [in] Die Quellkontext wie für die `IActiveScriptParse::ParseScriptText` oder `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Zeichen, die relativ zu Beginn der Skripttext versetzt.  
  
 `uNumChars`  
 [in] Anzahl der Zeichen in diesem Kontext.  
  
 `ppescc`  
 [out] Ein Enumerator, der Code Kontexte im angegebenen Bereich.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Smarthosts verwenden Sie diese Methode zum Delegieren der `IDebugDocumentContext::EnumCodeContexts` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptDebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)