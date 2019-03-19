---
title: IActiveScriptAuthor::GetScriptTextAttributes | Microsoft-Dokumentation
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
ms.openlocfilehash: 75e0d5edf7cf2f83e814036cec56a1b19a89813e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151933"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Gibt zurück, die Textattribute für einen Skriptblock.  
  
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
 [in, Size_is (`cch`)] der Text des Skriptblocks. Diese Zeichenfolge muss keine null-terminiert.  
  
 `cch`  
 [in] Die Größe des für die `pszCode` und `pattr` Parameter.  
  
 `pszDelimiter`  
 [in] Die Adresse des End-von-Script-Trennzeichens. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Scriptlets zu erkennen. Legen Sie diesen Parameter auf NULL, wenn es keine Trennzeichen ist, das das Ende der Skriptblock zu identifizieren.  
  
 `dwFlags`  
 [in] Die Flags, die Textattributen des Skriptblocks zugeordnet sind. Eine Kombination der folgenden Werte sind möglich:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifizieren von Bezeichnern, die das SOURCETEXT_ATTR_IDENTIFIER-Attribut aufweisen, und geben Sie Punktoperatoren, die das SOURCETEXT_ATTR_MEMBERLOOKUP-Attribut aufweisen.|  
|GETATTRFLAG_THIS|0x0100|Identifizieren Sie das aktuelle Objekt, das das SOURCETEXT_ATTR_THIS-Attribut aufweist.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifizieren Sie die Zeichenfolge Inhalt, und kommentieren Text, der das SOURCETEXT_ATTR_HUMANTEXT-Attribut aufweist.|  
  
 `pattr`  
 [in, out, Size_is (`cch`)] die Farbinformationen für den Skript-Block-Code.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)