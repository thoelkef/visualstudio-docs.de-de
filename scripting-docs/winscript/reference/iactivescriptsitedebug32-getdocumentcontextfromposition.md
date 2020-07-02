---
title: 'IActiveScriptSiteDebug32:: getdocumentcontextfromposition | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835276"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Wird von der Sprach-Engine zum Delegieren verwendet `IDebugCodeContext::GetSourceContext` .  
  
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
 in Der Quell Inhalt, der für oder bereitgestellt wird `ParseScriptText` `AddScriptlet` .  
  
 `uCharacterOffset`  
 in Zeichen Offset relativ zum Anfang des Skript Blocks oder Scriptlet.  
  
 `uNumChars`  
 in Anzahl der Zeichen in diesem Kontext.  
  
 `ppsc`  
 vorgenommen Der Dokument Kontext, der diesem Zeichen Positions Bereich entspricht.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode wurde erfolgreich ausgeführt.|  
  
## <a name="remarks"></a>Hinweise  
 Sprachmodule verwenden diese Methode, um zu delegieren `IDebugCodeContext::GetSourceContext` .  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebug32-Schnittstelle](../../winscript/reference/iactivescriptsitedebug32-interface.md)