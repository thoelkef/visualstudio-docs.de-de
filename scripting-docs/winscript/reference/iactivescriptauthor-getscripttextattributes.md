---
title: 'Iactivescriptauthor:: getscripttextattributes | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f89c7b654cc2ac7248598ee6498a3a290d17e2ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72563149"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Gibt die Text Attribute für einen Skriptblock zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCode`  
 [in, size_is (`cch`)] Der Text des Skript Blocks. Diese Zeichenfolge muss nicht NULL sein.  
  
 `cch`  
 in Die Größe, die für die `pszCode`-und `pattr` Parameter verwendet wird.  
  
 `pszDelimiter`  
 in Die Adresse des Trenn Zeichens für das Ende des Skripts. Wenn `pszCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen (z. b. zwei einfache Anführungszeichen), um das Ende des Scriptlets zu erkennen. Legen Sie diesen Parameter auf NULL fest, wenn es kein Trennzeichen gibt, um das Ende des Skript Blocks zu identifizieren.  
  
 `dwFlags`  
 in Die Flags, die den Textattributen des Skript Blocks zugeordnet sind. Kann eine Kombination der folgenden Werte sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifizieren Sie Bezeichner mit dem SOURCETEXT_ATTR_IDENTIFIER-Attribut, und identifizieren Sie Punkt Operatoren, die über das SOURCETEXT_ATTR_MEMBERLOOKUP-Attribut verfügen.|  
|GETATTRFLAG_THIS|0x0100|Identifizieren Sie das aktuelle-Objekt, das über das SOURCETEXT_ATTR_THIS-Attribut verfügt.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifizieren Sie Zeichen folgen Inhalt und Kommentartext, der über das SOURCETEXT_ATTR_HUMANTEXT-Attribut verfügt.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Die Farbinformationen für den Skriptblock Code.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptauthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)    
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)