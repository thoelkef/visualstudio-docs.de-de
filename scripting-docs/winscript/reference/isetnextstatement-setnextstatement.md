---
title: ISetNextStatement::SetNextStatement | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISetNextStatement.SetNextStatement
apilocation: scrobj.dll
ms.assetid: c5534f3b-39a5-4466-b8fc-69b717c6eee9
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21dafcd8cdb762e39f0cfcbde1162dd66c275ec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatementsetnextstatement"></a>ISetNextStatement::SetNextStatement
Diese Methode aktualisiert die nächsten Codekontext, den der Skriptinterpreter ausgeführt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 [in] Ein Zeiger auf ein Stack-Frame-Objekt.  
  
 `pCodeContext`  
 [in] Ein Zeiger auf ein Codeobjekt-Kontext.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [ISetNextStatement-Schnittstelle](../../winscript/reference/isetnextstatement-interface.md)