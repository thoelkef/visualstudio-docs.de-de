---
title: IActiveScriptDebug::GetScriptTextAttributes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 01218ba46de39dd8351ad82068ca4b34b52b0d46
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097387"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Gibt den Textattribute für ein beliebiger Speicherblock, der Skripttext zurück.  
  
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
 [in] Der Text des Skript-Block. Diese Zeichenfolge muss keine Null-terminiert sein.  
  
 `uNumCodeChars`  
 [in] Die Anzahl der Zeichen im Text-Block Skript.  
  
 `pstrDelimiter`  
 [in] Die Adresse des Trennzeichens Ende-des-Skript-Block. Wenn `pstrCode` wird analysiert, die aus einem Stream von Text und einem Trennzeichen, der Host in der Regel verwendet, wie z. B. zwei Anführungszeichen ("), um das Ende der Skriptblock erkennen einfache. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine-verwendet diese Informationen hängen von der Skript-Engine. Legen Sie diesen Parameter auf NULL, wenn der Host ein einzeln verwendetes Trennzeichen nicht verwendet haben, um das Ende des Skriptblocks markieren.  
  
 `dwFlags`  
 [in] Flags, die mit dem Skriptblock verknüpft ist. Es kann eine Kombination dieser Werte sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Gibt an, dass es sich bei Bezeichnern und Punktoperatoren mit den Flags SOURCETEXT_ATTR_IDENTIFIER und SOURCETEXT_ATTR_MEMBERLOOKUP bzw. identifiziert werden sollen.|  
|GETATTRFLAG_THIS|0x0100|Gibt an, dass der Bezeichner für das aktuelle Objekt mit dem Flag SOURCETEXT_ATTR_THIS identifiziert werden sollen.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Gibt an, dass der Inhalt, und kommentieren Zeichenfolgentext mit dem Flag SOURCETEXT_ATTR_HUMANTEXT identifiziert werden sollen.|  
  
 `pattr`  
 [in, out] Puffer, der die zurückgegebenen Attribute enthalten.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Smarthost, die implementiert `IDebugDocumentText` Schnittstelle kann diese Methode verwenden, delegieren Sie Aufrufe an die `IDebugDocumentText::GetText` Methode.  
  
 Diese Methode von Skriptblöcken die `GetScriptletTextAttributes` Methode eignet sich für Skriptlets.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptDebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)