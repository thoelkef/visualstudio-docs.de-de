---
title: 'Idebugdocumenthelper:: getscriptblockinfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a92aa00d7997ceccc583c88a070f6fbc7d4359d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576098"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Ruft den Bereich von Zeichen und das Skript Modul ab, das einem Skriptblock entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSourceContext`  
 in Der Quell Kontext für den Skriptblock.  
  
 `ppasd`  
 vorgenommen Die Skript-Engine für diesen Skriptblock.  
  
 `piCharPos`  
 vorgenommen Der Speicherort des Skript Blocks.  
  
 `cChars`  
 vorgenommen Anzahl der Zeichen im Skriptblock.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft den Bereich von Zeichen und das Skript Modul ab, das einem Skriptblock entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)