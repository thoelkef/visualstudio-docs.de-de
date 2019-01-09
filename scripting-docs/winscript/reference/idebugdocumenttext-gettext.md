---
title: IDebugDocumentText::GetText | Microsoft-Dokumentation
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
ms.openlocfilehash: 77cc255bcd04754cbfde4638b67a85f6fdc0a922
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091987"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Ruft ab, die Zeichen bzw. eine Zeichenposition Bereich zugeordneten Zeichenformate.  
  
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
 [in] Die Startposition des Zeichenbereichs Position folgt.  
  
 `pcharText`  
 [in, out] Einen Zeichenpuffer Text. Der Puffer muss groß genug für `cMaxChars` Zeichen. Wenn dieser Parameter NULL ist, gibt die Methode keine Zeichen zurück.  
  
 `pstaTextAttr`  
 [in, out] Einen Zeichenpuffer-Attribut. Der Puffer muss groß genug für `cMaxChars` Zeichen. Wenn dieser Parameter NULL ist, gibt die Methode keine Attribute zurück.  
  
 `pcNumChars`  
 [in, out] Die Anzahl der Zeichen/Attribute zurückgegeben. Dieser Parameter muss 0 (null) vor dem Aufrufen dieser Methode festgelegt werden.  
  
 `cMaxChars`  
 [in] Anzahl der Zeichen im Bereich Position. Außerdem gibt die maximale Anzahl der zurückzugebenden Zeichen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft die Zeichen bzw. eine Zeichenposition Bereich zugeordneten Zeichenformate ab. Bereich der Position wird mit einer Zeichenposition und eine Anzahl von Zeichen angegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)