---
title: 'Idebugdocumenttext:: gettext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572080"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Ruft die Zeichen und/oder die Zeichen Attribute ab, die einem Zeichen Positions Bereich zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
 in Start Position des Zeichen Positions Bereichs.  
  
 `pcharText`  
 [in, out] Ein Zeichen Text Puffer. Der Puffer muss groß genug sein, um `cMaxChars` Zeichen zu speichern. Wenn dieser Parameter NULL ist, gibt die Methode keine Zeichen zurück.  
  
 `pstaTextAttr`  
 [in, out] Ein Zeichen Attribut Puffer. Der Puffer muss groß genug sein, um `cMaxChars` Zeichen zu speichern. Wenn dieser Parameter NULL ist, gibt die Methode keine Attribute zurück.  
  
 `pcNumChars`  
 [in, out] Die Anzahl der zurückgegebenen Zeichen/Attribute. Dieser Parameter muss auf 0 (null) festgelegt werden, bevor diese Methode aufgerufen wird.  
  
 `cMaxChars`  
 in Anzahl der Zeichen im Zeichen Positions Bereich. Gibt auch die maximale Anzahl von Zeichen an, die zurückgegeben werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft die Zeichen und/oder die Zeichen Attribute ab, die einem Zeichen Positions Bereich zugeordnet sind. Der Zeichen Positions Bereich wird durch eine Zeichenposition und eine Anzahl von Zeichen angegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumenttext-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)