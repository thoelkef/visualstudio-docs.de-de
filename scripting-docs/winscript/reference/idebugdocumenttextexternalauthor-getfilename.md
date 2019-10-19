---
title: 'Idebugdocumenttextexternalauthor:: GetFilename | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetFileName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetFileName
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c07752d357a261fbc4800c3217a63d3de9489d55
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575973"
---
# <a name="idebugdocumenttextexternalauthorgetfilename"></a>IDebugDocumentTextExternalAuthor::GetFileName
Gibt den Namen des Dokuments ohne Pfadinformationen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrShortName`  
 vorgenommen Zeichenfolge, die den Kurznamen des Dokuments enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den Namen des Dokuments ohne Pfadinformationen zurück. Der Kurzname wird in der Regel in Dialogfeldern verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextExternalAuthor-Schnittstelle](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)