---
title: IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa96623b4356f0a3d17c8b2631840953dac2d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Gibt die Textattribute für einen Skriptblock.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in Size_is (`cch`)] der Text des Skriptblocks. Diese Zeichenfolge keine null-terminiert.  
  
 `cch`  
 [in] Die Größe des für die `pszCode` und `pattr` Parameter.  
  
 `pszDelimiter`  
 [in] Die Adresse der das Ende des Skript-Trennzeichen. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Scriptlets zu erkennen. Legen Sie diesen Parameter auf NULL, wenn es keine Trennzeichen ist, das das Ende der Skriptblock zu identifizieren.  
  
 `dwFlags`  
 [in] Die Flags, die Textattributen des Skriptblocks zugeordnet sind. Eine Kombination der folgenden Werte ist möglich:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Identifizieren Sie Bezeichner, die mit dem SOURCETEXT_ATTR_IDENTIFIER-Attribut enthalten, und identifizieren Sie Punktoperatoren, die das SOURCETEXT_ATTR_MEMBERLOOKUP-Attribut aufweisen.|  
|GETATTRFLAG_THIS|0 x 0100|Identifizieren Sie das aktuelle Objekt, das das SOURCETEXT_ATTR_THIS-Attribut aufweist.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Identifizieren Sie die Zeichenfolge Inhalt und einen Kommentar Text, der das SOURCETEXT_ATTR_HUMANTEXT-Attribut aufweist.|  
  
 `pattr`  
 [in, out Size_is (`cch`)] die Farbinformationen für Skriptblockcode.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)