---
title: Getscripttextattributes | Microsoft-Dokumentation
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
ms.openlocfilehash: 6a5e56468e51f6d90e37e90c885b6b9df48d5f6e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158996"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Gibt die Textattribute für einen Textblock Dokument zurück.  
  
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
 [in] Der Text des Skript-Block. Diese Zeichenfolge muss es sich nicht auf null-terminiert.  
  
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
|GETATTRFLAG_HUMANTEXT|0x8000|Gibt an, dass der Inhalt, und kommentieren Zeichenfolgentext mit dem Flag SOURCETEXT_ATTR_HUMANTEXT identifiziert werden sollen.|  
  
 `pattr`  
 [in, out] Puffer, der die zurückgegebenen Attribute enthalten.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Host wird nur für die Standardattribute verwendet.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt die Textattribute für ein beliebiger Speicherblock, der Dokumenttext. Für Hosts zurückzugebenden akzeptabel ist `E_NOTIMPL`, in diesem Fall die Standardattribute verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)