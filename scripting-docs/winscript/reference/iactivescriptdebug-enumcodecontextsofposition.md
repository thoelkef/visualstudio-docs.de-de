---
title: 'Iactivescriptdebug:: enumcodecontextsofposition | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: aedfe5d40d8f4086e30f3a62c070b8ccd5ef2388
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572783"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Wird von einem Smarthost verwendet, um die `IDebugDocumentContext::EnumCodeContexts`-Methode zu delegieren.  
  
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
 in Der Quell Kontext, der für `IActiveScriptParse::ParseScriptText` oder `IActiveScriptParse::AddScriptlet` bereitgestellt wird.  
  
 `uCharacterOffset`  
 in Zeichen Offset relativ zum Anfang des Skript Texts.  
  
 `uNumChars`  
 in Anzahl der Zeichen in diesem Kontext.  
  
 `ppescc`  
 vorgenommen Ein Enumerator der Code Kontexte im angegebenen Bereich.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Smart Hosts verwenden diese Methode, um die `IDebugDocumentContext::EnumCodeContexts`-Methode zu delegieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptdebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)    
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)