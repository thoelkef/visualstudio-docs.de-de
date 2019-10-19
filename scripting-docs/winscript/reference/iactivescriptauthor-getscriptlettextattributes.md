---
title: 'Iactivescriptauthor:: getscriptlettextattributes | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576172"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Gibt die Text Attribute eines Scriptlet zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCode`  
 [in, size_is (`cch`)] Der Scriptlet-Text. Diese Zeichenfolge muss nicht NULL sein.  
  
 `cch`  
 in Die Größe, die für die `pszCode`-und `pattr` Parameter verwendet wird.  
  
 `pszDelimiter`  
 in Die Adresse des End-of-Scriptlet-Trenn Zeichens. Wenn `pszCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen (z. b. zwei einfache Anführungszeichen), um das Ende des Scriptlets zu erkennen. Legen Sie diesen Parameter auf NULL fest, wenn kein Trennzeichen verwendet wird, um das Ende des Scriptlets zu identifizieren.  
  
 `dwFlags`  
 in Die Flags, die den Textattributen des Scriptlet zugeordnet sind. Kann eine Kombination der folgenden Werte sein.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifizieren Sie Bezeichner mit dem SOURCETEXT_ATTR_IDENTIFIER-Attribut, und identifizieren Sie Punkt Operatoren, die über das SOURCETEXT_ATTR_MEMBERLOOKUP-Attribut verfügen.|  
|GETATTRFLAG_THIS|0x0100|Identifizieren Sie das aktuelle-Objekt, das über das SOURCETEXT_ATTR_THIS-Attribut verfügt.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifizieren Sie Zeichen folgen Inhalt und Kommentartext, der über das SOURCETEXT_ATTR_HUMANTEXT-Attribut verfügt.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Die Farbinformationen für den Scriptlet-Code.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptauthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)    
 [Iactivescriptauthor:: getscripttextattributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)    
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)