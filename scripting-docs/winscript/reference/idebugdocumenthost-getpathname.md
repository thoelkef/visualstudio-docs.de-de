---
title: 'Idebugdocumenthost:: getPathname | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33ebcde4cf1db28e199f13fae720374bd1b64763
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569280"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Gibt den vollständigen Pfad und den Dateinamen der Quelldatei des Dokuments zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrLongName`  
 vorgenommen Eine Zeichenfolge, die den langen Namen enthält.  
  
 `pfIsOriginalFile`  
 vorgenommen Ein Flag, das true ist, wenn `pbstrLongName` auf die ursprüngliche Datei für das Dokument verweist, andernfalls false.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Es kann keine Quelldatei erstellt oder bestimmt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den vollständigen Pfad und den Dateinamen der Quelldatei des Dokuments zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)