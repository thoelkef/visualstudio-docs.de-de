---
title: 'Iactivescriptdebug:: getscripttextattributes | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57bd466965f6431a1418df1aa56cf6a7bbbc78cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576930"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Gibt die Text Attribute für einen beliebigen Block von Skript Text zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrCode`  
 in Der Skriptblock Text. Diese Zeichenfolge muss nicht NULL sein.  
  
 `uNumCodeChars`  
 in Die Anzahl der Zeichen im Skriptblock Text.  
  
 `pstrDelimiter`  
 in Adresse des Trenn Zeichens für das Ende des Skript Blocks. Wenn `pstrCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen, z. b. zwei einfache Anführungszeichen (' '), um das Ende des Skript Blocks zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter auf NULL fest, wenn der Host kein Trennzeichen verwendet hat, um das Ende des Skript Blocks zu markieren.  
  
 `dwFlags`  
 in Flags, die dem Skriptblock zugeordnet sind. Es kann eine Kombination dieser Werte sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Gibt an, dass Bezeichner und Punkt Operatoren mit den SOURCETEXT_ATTR_IDENTIFIER-bzw. SOURCETEXT_ATTR_MEMBERLOOKUP Flags identifiziert werden sollen.|  
|GETATTRFLAG_THIS|0x0100|Gibt an, dass der Bezeichner für das aktuelle Objekt mit dem SOURCETEXT_ATTR_THIS-Flag identifiziert werden soll.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Gibt an, dass Zeichen folgen Inhalt und Kommentartext mit dem SOURCETEXT_ATTR_HUMANTEXT-Flag identifiziert werden sollen.|  
  
 `pattr`  
 [in, out] Puffer, der die zurückgegebenen Attribute enthalten soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein intelligenter Host, der `IDebugDocumentText`-Schnittstelle implementiert, kann diese Methode zum Delegieren von Aufrufen an die `IDebugDocumentText::GetText`-Methode verwenden.  
  
 Diese Methode für Skriptblöcke. die `GetScriptletTextAttributes`-Methode wird für Scriptlets verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptdebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Idebugdocumenttext-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)