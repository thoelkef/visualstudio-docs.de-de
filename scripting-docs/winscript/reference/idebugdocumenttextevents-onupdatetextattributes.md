---
title: IDebugDocumentTextEvents::onUpdateTextAttributes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateTextAttributes
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c2e5624e7cbefdca929a11b75f0273337fab30c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097161"
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
Gibt an, dass der Bereich der zugrunde liegenden Position zugeordnete Textattribute geändert haben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cCharacterPosition`  
 [in] Die Zeichenposition des ersten Zeichens, die die Attribute geändert wurden.  
  
 `cNumToUpdate`  
 [in] Die Anzahl der Zeichen im Bereich.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt an, dass der Bereich der zugrunde liegenden Position zugeordnete Textattribute geändert haben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextEvents-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)