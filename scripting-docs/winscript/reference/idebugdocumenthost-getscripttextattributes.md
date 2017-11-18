---
title: IDebugDocumentHost::GetScriptTextAttributes | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 517b228bb46594d19ba6d2fdf41a68e22ac03c75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Gibt den Textattribute für einen Textblock Dokument zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Der Skripttext Block. Diese Zeichenfolge muss nicht null-terminiert.  
  
 `uNumCodeChars`  
 [in] Die Anzahl der Zeichen im Text Skript-Block.  
  
 `pstrDelimiter`  
 [in] Die Adresse des Trennzeichens zum Ende der Skriptblock. Wenn `pstrCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen, z. B. zwei Anführungszeichen ("), um das Ende des Skriptblocks erkennen einfache. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass dem Skriptmodul in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) das scripting Modul verwendet diese Informationen hängen von dem Skriptmodul. Legen Sie diesen Parameter auf NULL, wenn der Host ein Trennzeichen nicht verwendet haben, um das Ende des Skriptblocks markieren.  
  
 `dwFlags`  
 [in] Flags, die mit dem Skriptblock verknüpft sind. Es kann eine Kombination dieser Werte sein:  
  
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
|`E_NOTIMPL`|Der Host wird nur für die Standardattribute verwendet.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt die Textattribute für einen beliebigen TextBlock Dokument zurück. Für Hosts zurückzugebenden akzeptabel ist `E_NOTIMPL`, in diesem Fall die Standardattribute verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)