---
title: IDebugDocumentHost::GetPathName | Microsoft-Dokumentation
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
ms.openlocfilehash: 09e36411cdd378e78ac3bc59df5330eb8ecb47b6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160575"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Gibt den vollständigen Pfad und Namen der Quelldatei des Dokuments zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrLongName`  
 [out] Eine Zeichenfolge, die den langen Namen enthält.  
  
 `pfIsOriginalFile`  
 [out] Ein Flag, true, wenn `pbstrLongName` bezieht sich auf die ursprüngliche Datei für das Dokument, "false" andernfalls.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Keine Quelldatei kann erstellt oder festgelegt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den vollständigen Pfad und Namen der Quelldatei des Dokuments ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)