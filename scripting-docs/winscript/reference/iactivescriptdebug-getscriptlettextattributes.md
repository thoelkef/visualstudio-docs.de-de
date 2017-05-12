---
title: "IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptletTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptletTextAttributes"
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptletTextAttributes
Gibt die Textattribute für ein beliebiges Skriptlet zurück.  
  
## Syntax  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### Parameter  
 `pstrCode`  
 \[in\] Der Skriptlettext.  Diese Zeichenfolge muss, nicht NULL sein beendet.  
  
 `uNumCodeChars`  
 \[in\] Die Anzahl von Zeichen im Skriptlettext.  
  
 `pstrDelimiter`  
 \[in\] Ende\-vonSkriptlet Adresse des Trennzeichens.  Wenn `pstrCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen, wie zwei einfache Anführungszeichen \("\), um das Ende des Skriptlets zu erkennen.  Dieser Parameter gibt das Trennzeichen an, den der Host verwendet, das Skriptmodul zulassen, um eine bedingte Vorverarbeiten von Primitiva bereitzustellen, \(beispielsweise ein einfaches Anführungszeichen \['\] mit zwei einfachen Anführungszeichen zur Verwendung als Trennzeichen\) ersetzt wird.  Genauer gesagt, wie \(und ob\) das Skriptmodul verwendet, sind diese Informationen im Skriptmodul ab.  Legen Sie diesen Parameter auf fest, um auf NULL, wenn der Host kein Trennzeichen verwendet, um das Ende des Skriptlets zu markieren.  
  
 `dwFlags`  
 \[in\] Flags in Zusammenhang mit dem Skriptlet.  Kann eine Kombination dieser Werte:  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Gibt an, dass Bezeichner und Punktoperatoren mit den SOURCETEXT\_ATTR\_IDENTIFIER\- und SOURCETEXT\_ATTR\_MEMBERLOOKUP\-Flags identifiziert werden sollen, bzw. an.|  
|GETATTRFLAG\_THIS|0x0100|Gibt an, dass der Bezeichner für das aktuelle Objekt mit dem SOURCETEXT\_ATTR\_THIS\-Flag identifiziert werden soll.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Gibt an, dass Zeichenfolgeninhalt und Kommentartext identifiziert werden sollten mit dem SOURCETEXT\_ATTR\_HUMANTEXT\-Flag.|  
  
 `pattr`  
 \[in, out\] Puffer, um die zurückgegebenen Attribute zu enthalten.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Ein Smarthost, der `IDebugDocumentText`\-Schnittstelle implementiert, kann diese Methode verwenden, um Aufrufe der `IDebugDocumentText::GetText`\-Methode zu delegieren.  
  
 Dieser Aufruf wird bereitgestellt, da Skriptlets möglicherweise tendieren, Ausdrücke sein und eine andere Syntax als ein Skriptblock haben.  Wenn sie dieselbe Syntax haben, ist die Implementierung dieser Methode zur Implementierung der `GetScriptTextAttributes`\-Methode identisch.  
  
## Siehe auch  
 [IActiveScriptDebug\-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText\-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE\_TEXT\_ATTR\-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)