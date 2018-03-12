---
title: IDebugDocumentHelper::CreateDebugDocumentContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.CreateDebugDocumentContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::CreateDebugDocumentContext
ms.assetid: aa4ec691-9fb1-4da7-8085-b40d8a062467
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54d91c4df9d1e478d028e95e5cfc930d69355c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpercreatedebugdocumentcontext"></a>IDebugDocumentHelper::CreateDebugDocumentContext
Erstellt einen neuen Kontext der Debug-Dokument.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CreateDebugDocumentContext(  
   ULONG                    iCharPos,  
   ULONG                    cChars,  
   IDebugDocumentContext**  ppddc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `iCharPos`  
 [in] Der Speicherort des Beginns der Inhalt des Debug-Dokuments.  
  
 `cChars`  
 [in] Anzahl der Zeichen im Kontext.  
  
 `ppddc`  
 [out] Der neue Kontext der Debug-Dokument.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht den Host, ein neuer Kontext der Debug-Dokument erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)