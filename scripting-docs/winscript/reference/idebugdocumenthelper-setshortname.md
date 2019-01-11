---
title: IDebugDocumentHelper::SetShortName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetShortName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetShortName
ms.assetid: 811a444b-0ea4-4374-9d4c-4f7713bdd1ff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7014ecc858734a4dea6f9c4c2453f101c28d8996
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089933"
---
# <a name="idebugdocumenthelpersetshortname"></a>IDebugDocumentHelper::SetShortName
Legt den kurzen Namen für das Dokument fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetShortName(  
   LPCOLESTR  pszShortName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszShortName`  
 [in] Eine mit Null endende Zeichenfolge, die den kurzen Namen des Dokuments enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode legt einen neuen kurzen Namen für das Dokument.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)