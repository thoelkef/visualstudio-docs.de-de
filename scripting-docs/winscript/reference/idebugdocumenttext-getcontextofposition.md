---
title: IDebugDocumentText::GetContextOfPosition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetContextOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2eb889bef17d2038f17c7f8618ad65ca2162f0c7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097590"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
Erstellt ein Dokument Context-Objekt, dem Bereich der angegebenen Position entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cCharacterPosition`  
 [in] Die Startposition des Zeichenbereichs Position folgt.  
  
 `cNumChars`  
 [in] Anzahl der Zeichen im Bereich.  
  
 `ppsc`  
 [out] Das Dokument-Kontextobjekt Bereich der angegebenen Position entspricht.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt ein Dokument Context-Objekt, dem Bereich der angegebenen Position entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)