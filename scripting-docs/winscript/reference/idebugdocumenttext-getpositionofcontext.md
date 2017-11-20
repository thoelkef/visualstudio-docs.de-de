---
title: IDebugDocumentText::GetPositionOfContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetPositionOfContext
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetPositionOfContext
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f843d71096dea4c22eda757a4d6975dfda94180
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetpositionofcontext"></a>IDebugDocumentText::GetPositionOfContext
Gibt die Zeichenposition Bereich für eine Dokumentenkontext zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `psc`  
 [in] Das Dokumentobjekt Kontext.  
  
 `pcCharacterPosition`  
 [out] Die Startposition des Zeichenbereichs folgt Position.  
  
 `cNumChars`  
 [out] Anzahl der Zeichen im Bereich.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Der Dokumentenkontext für diese Methode muss mit diesem Dokument zugeordnet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)