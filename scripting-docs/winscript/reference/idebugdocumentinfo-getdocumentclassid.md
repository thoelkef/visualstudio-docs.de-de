---
title: IDebugDocumentInfo::GetDocumentClassId | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f43f3dbf76c9055bc4e521435ab56b1c7c6e40
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086761"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
Gibt eine `CLSID` Identifizieren des Dokumenttyps.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pclsidDocument`  
 [out] Ein `CLSID` Identifizieren des Dokumenttyps.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht die Debugger-IDE auf dem Host benutzerdefinierten Viewer für dieses Dokument.  
  
 Wenn das Dokument nicht angezeigt werden sollen, den Rückgabewert verfügt `pclsidDocument` ist `CLSID_NULL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentInfo-Schnittstelle](../../winscript/reference/idebugdocumentinfo-interface.md)