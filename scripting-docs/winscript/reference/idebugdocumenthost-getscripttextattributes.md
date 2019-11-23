---
title: 'Idebugdocumerthost:: getscripttextattributes | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b18f4f49fa157b78e4f1fd6c7766e929890a6c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569200"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Gibt die Text Attribute für einen Block von Dokument Text zurück.  
  
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
|`E_NOTIMPL`|Der Host verwendet nur Standard Attribute.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt die Text Attribute für einen beliebigen Block von Dokument Text zurück. Es ist zulässig, dass Hosts `E_NOTIMPL`zurückgeben. in diesem Fall werden die Standard Attribute verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumeinthost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)