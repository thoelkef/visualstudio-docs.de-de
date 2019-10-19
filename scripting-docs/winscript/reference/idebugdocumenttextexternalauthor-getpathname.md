---
title: 'Idebugdocumenttextexternalauthor:: getPathname | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e876b41ce1bde4defffd11267c6665f9d57da077
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575968"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Gibt den vollständigen Pfad und den Dateinamen des Dokuments zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrLongName`  
 vorgenommen Zeichenfolge, die den vollständigen Pfad und den Dateinamen enthält.  
  
 `pfIsOriginalFile`  
 vorgenommen Boolescher Wert, der angibt, ob der Pfad und der Dateiname auf das ursprüngliche Dokument verweisen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Quelldatei kann nicht erstellt oder bestimmt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den vollständigen Pfad und den Dateinamen des Dokuments zurück.  
  
 Wenn `pfIsOriginalFile` false ist, beziehen sich der Pfad und der Dateiname in `pbstrLongName` auf eine neu erstellte temporäre Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextExternalAuthor-Schnittstelle](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)