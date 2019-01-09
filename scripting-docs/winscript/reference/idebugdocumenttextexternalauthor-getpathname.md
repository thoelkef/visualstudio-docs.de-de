---
title: IDebugDocumentTextExternalAuthor::GetPathName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e17d27a320eac95445c083c718f5abcebbbc46cf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088841"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Gibt den vollständigen Pfad und Dateiname den Namen des Dokuments zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrLongName`  
 [out] Eine Zeichenfolge mit den vollständigen Pfad und Namen.  
  
 `pfIsOriginalFile`  
 [out] Boolescher Wert, der angibt, ob der Pfad und Dateiname der Name bezieht sich auf das ursprüngliche Dokument.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Quelldatei kann nicht erstellt oder festgelegt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den vollständigen Pfad und Dateiname den Namen des Dokuments.  
  
 Wenn `pfIsOriginalFile` ist "false", den Pfad und Dateinamen in `pbstrLongName` finden Sie in eine neu erstellte temporäre Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextExternalAuthor-Schnittstelle](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)