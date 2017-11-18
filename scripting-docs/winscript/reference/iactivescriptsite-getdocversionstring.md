---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Ruft eine Host definierte Zeichenfolge, die die aktuelle Dokumentversion eindeutig identifiziert. Wenn das zugehörige Dokument außerhalb des Bereichs der Windows-Skript (wie im Fall einer HTML-Seite, die bearbeitet wird, mit dem Editor) geändert wurde, kann das Skriptmodul speichern Sie diese zusammen mit den beibehaltenen Zustand durch Erzwingen einer erneuten Kompilierung das nächste Mal, das des Skripts laden.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrVersionString`  
 [out] Die Adresse der Versionszeichenfolge Dokument Host definiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_NOTIMPL` Wenn diese Methode nicht unterstützt wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `E_NOTIMPL` zurückgegeben wird, wird das Skriptmodul sollten davon ausgehen, dass das Skript mit dem das Dokument synchronisiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)