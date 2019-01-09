---
title: IDebugDocumentHost::GetFileName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetFileName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetFileName
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55b3518b6d73793df712ed9deccb5e27c320a9d6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097148"
---
# <a name="idebugdocumenthostgetfilename"></a>IDebugDocumentHost::GetFileName
Gibt den Namen des Dokuments ohne Pfadinformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrShortName`  
 [out] Eine Zeichenfolge, die den kurzen Namen des Dokuments enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den kurzen Namen des Dokuments ohne Pfadinformationen. Der kurze Name wird in der Regel wie z. B. in Situationen verwendet die **speichern unter...**  Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)