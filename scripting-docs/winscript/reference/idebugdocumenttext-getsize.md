---
title: IDebugDocumentText::GetSize | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95f8df44a503fa72f57a9cee17eb5e832e4eb670
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153996"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Gibt die Anzahl der Zeilen und die Anzahl der Zeichen im Dokument zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcNumLines`  
 [out] Anzahl der Zeilen im Dokument. Wenn dieser Parameter NULL ist, wird die Methode keinen Wert zurückgibt.  
  
 `pcNumChars`  
 [out] Anzahl der Zeichen im Dokument. Wenn dieser Parameter NULL ist, wird die Methode keinen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt die Anzahl der Zeilen und die Anzahl der Zeichen im Dokument zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)