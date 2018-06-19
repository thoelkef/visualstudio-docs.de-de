---
title: IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909879030e5c6d26353d2003279d5c1ca7bacb74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724430"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Gibt den Textattribute für eine beliebige Scriptlet zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrCode`  
 [in] Das Scriptlet-Texts. Diese Zeichenfolge muss nicht mit Null-terminiert sein.  
  
 `uNumCodeChars`  
 [in] Die Anzahl der Zeichen im Scriptlet-Texts.  
  
 `pstrDelimiter`  
 [in] Adresse des end-of-scriptlet-Trennzeichens. Wenn `pstrCode` von einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen, wie beispielsweise zwei einfache Anführungszeichen ("), um das Ende des Scriptlets zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass dem Skriptmodul in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) das scripting Modul verwendet diese Informationen hängen von dem Skriptmodul. Legen Sie diesen Parameter auf NULL, wenn der Host ein Trennzeichen nicht verwendet haben, um das Ende des Scriptlets zu markieren.  
  
 `dwFlags`  
 [in] Flags, die dem Scriptlet zugeordnet sind. Es kann eine Kombination dieser Werte sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Gibt an, dass es sich bei Bezeichnern und Punktoperatoren mit den Flags SOURCETEXT_ATTR_IDENTIFIER und SOURCETEXT_ATTR_MEMBERLOOKUP bzw. identifiziert werden sollen.|  
|GETATTRFLAG_THIS|0 x 0100|Gibt an, dass der Bezeichner für das aktuelle Objekt mit dem Flag SOURCETEXT_ATTR_THIS identifiziert werden sollen.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Gibt an, dass Inhalte und einen Kommentar Zeichenfolgentext mit dem Flag SOURCETEXT_ATTR_HUMANTEXT identifiziert werden sollen.|  
  
 `pattr`  
 [in, out] Puffer, in die zurückgegebenen Attribute enthalten.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Smarthost, die implementiert `IDebugDocumentText` Schnittstelle kann verwenden Sie diese Methode zum Delegieren von Aufrufen an die `IDebugDocumentText::GetText` Methode.  
  
 Dieser Aufruf wird bereitgestellt, da Skriptlets tendenziell Ausdrücke sein, und möglicherweise eine andere Syntax als einen Skriptblock. Wenn sie die gleiche Syntax aufweisen, wird die Implementierung dieser Methode für eine Implementierung der identisch sein die `GetScriptTextAttributes` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptDebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)