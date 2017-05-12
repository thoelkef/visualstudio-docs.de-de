---
title: "IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetInfoFromContext"
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::GetInfoFromContext
EINGABETASTE Typinformationen und Anchorpositionen für ein bestimmtes Zeichen in einem Codeblock.  Dies stellt Informationen für Member IntelliSense, globale Listen und Parametertipps bereit.  
  
## Syntax  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### Parameter  
 `pszCode`  
 \[in\] Ergibt sich die Adresse der Codeblockzeichenfolge, die verwendet wird, um die Informationen zu generieren.  
  
 `cchCode`  
 \[in\] Die Länge des Codeblocks.  
  
 `ichCurrentPosition`  
 \[in\] Die Zeichenstelle relativ zum Anfang des Blocks.  
  
 `dwListTypesRequested`  
 \[in\] Die Listentypen angefordert.  Kann eine Kombination der folgenden Werte:  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|SCRIPT\_CMPL\_NOLIST|0x0000|Keine Liste.|  
|SCRIPT\_CMPL\_MEMBERLIST|0x0001|Memberliste.|  
|SCRIPT\_CMPL\_ENUMLIST|0x0002|Enumerationsliste.|  
|SCRIPT\_CMPL\_PARAMLIST|0x0004|Aufrufsmethodenparameterliste.|  
|SCRIPT\_CMPL\_GLOBALLIST|0x0008|Globale Liste.|  
  
 Der SCRIPT\_CMPL\_GLOBALLIST\-Typ wird als Standard Abschlusselement behandelt, das kombiniert werden kann, indem die OR\-Operator mit anderen Abschlusselementen verwendet.  Das Skripterstellungsmodul versucht zuerst, Typinformationen für andere Vervollständigungslistenelemente aufzufüllen.  Wenn dies fehlschlägt, füllt das Modul für SCRIPT\_CMPL\_GLOBALLIST auf.  
  
 `pdwListTypesProvided`  
 \[out\] Der Typ der Liste bereitgestellt.  
  
 `pichListAnchorPosition`  
 \[out\] Der Startindex des Kontexts, der die aktuelle Position enthält.  Der Startindex ist relativ zum Anfang des Blocks.  
  
 Dies wird nur aufgefüllt, wenn `dwListTypesRequested` SCRIPT\_CMPL\_MEMBERLIST, SCRIPT\_CMPL\_ENUMLIST oder SCRIPT\_CMPL\_GLOBALLIST einschließt.  Für andere angeforderte Listentypen ist das Ergebnis nicht definiert.  
  
 `pichFuncAnchorPosition`  
 \[out\] Der Startindex des Funktionsaufrufs, der die aktuelle Position enthält.  Der Startindex ist relativ zum Anfang des Blocks.  
  
 Dies wird nur aufgefüllt, wenn der Kontext, der die aktuelle Position enthält, einen Funktionsaufruf ist und wenn `dwListTypesRequested` SCRIPT\_CMPL\_PARAMLIST einschließt.  Andernfalls wird das Ergebnis nicht definiert.  
  
 `pmemid`  
 \[out\] Das MEMBERID der Funktion, wie durch einen Typ im Parameter `IProvideMultipleClassInfo``ppunk` out definiert.  
  
 Dies wird nur aufgefüllt, wenn `dwListTypesRequested` SCRIPT\_CMPL\_PARAMLIST einschließt.  
  
 `piCurrentParameter`  
 \[out\] Der Index des Parameters, der die aktuelle Position enthält.  Wenn die aktuelle Position im Funktionsnamen ist, wird \-1 zurückgegeben.  
  
 Der Wert `piCurrentParameter` wird nur aufgefüllt, wenn `dwListTypesRequested` SCRIPT\_CMPL\_PARAMLIST einschließt.  
  
 `ppunk`  
 Die Typinformationen, die in Form eines Objekts `IProvideMultipleClassInfo` bereitgestellt wird.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideMultipleClassInfo>   
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)