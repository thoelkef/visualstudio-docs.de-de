---
title: IDebugDocumentTextEvents::onDestroy | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onDestroy
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onDestroy
ms.assetid: 1b7eb341-6bad-403f-9821-19112f8732f3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 137329e48f6cb36e36f0196fa226303468eec88a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946751"
---
# <a name="idebugdocumenttexteventsondestroy"></a>IDebugDocumentTextEvents::onDestroy
Gibt an, dass das zugrunde liegende Dokument wurde gelöscht, und nicht mehr gültig ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onDestroy();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt an, dass das zugrunde liegende Dokument wurde gelöscht, und nicht mehr gültig ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextEvents-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)