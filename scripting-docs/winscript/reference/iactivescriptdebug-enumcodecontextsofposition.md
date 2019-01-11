---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft-Dokumentation
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
ms.openlocfilehash: abca643dc4e18f786421959c20804a28cf54ec7b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097174"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Die ein Smarthost für das Delegieren der `IDebugDocumentContext::EnumCodeContexts` Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSourceContext`  
 [in] Die Quellkontext Sie `IActiveScriptParse::ParseScriptText` oder `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Zeichen, die relativ zum Beginn der Skripttext offset.  
  
 `uNumChars`  
 [in] Anzahl der Zeichen in diesem Kontext.  
  
 `ppescc`  
 [out] Ein Enumerator, der die Codekontexte im angegebenen Bereich.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Smart Hosts verwenden Sie diese Methode delegiert die `IDebugDocumentContext::EnumCodeContexts` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptDebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)