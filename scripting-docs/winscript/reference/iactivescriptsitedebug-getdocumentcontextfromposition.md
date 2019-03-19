---
title: Getdocumentcontextfromposition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df6c59fea5cfd60b6ae9a1b34e7000bd38dd9920
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147124"
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
Die Sprach-Engine, die für die Delegieren `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSourceContext`  
 [in] Der Quellinhalt Sie `ParseScriptText` oder `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Offset relativ zum Beginn des Skriptblocks oder Scriptlet-Zeichen.  
  
 `uNumChars`  
 [in] Anzahl der Zeichen in diesem Kontext.  
  
 `ppsc`  
 [out] Der Dokumentenkontext für diesen Bereich Position des Zeichens.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sprach-Engines verwenden Sie diese Methode delegiert `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebug-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)