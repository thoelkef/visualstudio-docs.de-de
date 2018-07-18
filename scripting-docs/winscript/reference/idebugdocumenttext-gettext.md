---
title: IDebugDocumentText::GetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728080"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Ruft ab, die Zeichen und/oder die Attribute des Zeichens einem Zeichenposition Bereich zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cCharacterPosition`  
 [in] Die Startposition des Zeichenbereichs folgt Position.  
  
 `pcharText`  
 [in, out] Text-Zeichenpuffer. Der Puffer muss groß genug für `cMaxChars` Zeichen. Wenn dieser Parameter NULL ist, gibt die Methode keinen Zeichen zurück.  
  
 `pstaTextAttr`  
 [in, out] Ein Attribut Zeichenpuffer. Der Puffer muss groß genug für `cMaxChars` Zeichen. Wenn dieser Parameter NULL ist, gibt die Methode keinen Attribute zurück.  
  
 `pcNumChars`  
 [in, out] Die Anzahl der Zeichen/Attribute zurückgegeben. Dieser Parameter muss vor dem Aufrufen dieser Methode auf NULL festgelegt werden.  
  
 `cMaxChars`  
 [in] Anzahl der Zeichen im Bereich Position. Außerdem gibt die maximale Anzahl der zurückzugebenden Zeichen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft die Zeichen und/oder die Attribute des Zeichens einem Zeichenposition Bereich zugeordnet. Die Position Zeichenbereich wird von einer Zeichenposition und eine Anzahl von Zeichen angegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)