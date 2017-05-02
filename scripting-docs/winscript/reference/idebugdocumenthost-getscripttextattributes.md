---
title: "IDebugDocumentHost::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetScriptTextAttributes"
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetScriptTextAttributes
Gibt die Textattribute für einen Block Dokumenttext zurück.  
  
## Syntax  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### Parameter  
 `pstrCode`  
 \[in\] Der Skriptblocktext.  Diese Zeichenfolge muss nicht, um NULL sein beendet.  
  
 `uNumCodeChars`  
 \[in\] Die Anzahl von Zeichen im Skriptblocktext.  
  
 `pstrDelimiter`  
 \[in\] Ende\-von\-SkriptBlock Adresse des Trennzeichens.  Wenn `pstrCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen, wie zwei einfache Anführungszeichen \("\), um das Ende des Skriptblocks zu erkennen.  Dieser Parameter gibt das Trennzeichen an, den der Host verwendet, das Skriptmodul zulassen, um eine bedingte Vorverarbeiten von Primitiva bereitzustellen, \(beispielsweise ein einfaches Anführungszeichen \['\] mit zwei einfachen Anführungszeichen zur Verwendung als Trennzeichen\) ersetzt wird.  Genauer gesagt, wie \(und ob\) das Skriptmodul verwendet, sind diese Informationen im Skriptmodul ab.  Legen Sie diesen Parameter auf fest, um auf NULL, wenn der Host kein Trennzeichen verwendet, um das Ende des Skriptblocks zu markieren.  
  
 `dwFlags`  
 \[in\] Flags in Zusammenhang mit dem Skriptblock.  Kann eine Kombination dieser Werte:  
  
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
|`E_NOTIMPL`|Der Host verwendet nur Standardattribute.|  
  
## Hinweise  
 Diese Methode gibt die Textattribute für einen beliebigen Block Dokumenttext zurück.  Es ist zulässig für Hosts, `E_NOTIMPL` zurückzugeben, in diesem Fall die Standardattribute verwendet werden.  
  
## Siehe auch  
 [IDebugDocumentHost\-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE\_TEXT\_ATTR\-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)