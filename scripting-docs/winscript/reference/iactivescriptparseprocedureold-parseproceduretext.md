---
title: "IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld::ParseProcedureText"
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld::ParseProcedureText
Analysiert die angegebene Kennzahlprozedur und eine anonyme Prozedur dem Namespace hinzu.  
  
## Syntax  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### Parameter  
 `pstrCode`  
 \[in\] Der Prozedurtext auszuwerten.  Die Interpretation dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrFormalParams`  
 \[in\] Namen des formalen Parameters für die Prozedur.  Die Parameternamen müssen mit den entsprechenden Trennzeichen für das Skriptmodul getrennt werden.  Die Namen dürfen nicht in Klammern eingeschlossen werden.  
  
 `pstrItemName`  
 \[in\] Der Name des benannten Elements, das den Kontext gibt, in der die Prozedur ausgewertet werden soll.  Wenn dieser Parameter `NULL` ist, wird der Code in den globalen Kontext des Skriptmoduls ausgewertet.  
  
 `punkContext`  
 \[in\] Das Kontextobjekt.  Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solches Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen.  Wenn dieser Parameter `NULL` ist, verwendet das Modul `pstrItemName`, um den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 \[in\] Das Ende\-vonProzedur Trennzeichen.  Wenn `pstrCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen, wie zwei einfache Anführungszeichen \("\), um das Ende der Prozedur zu erkennen.  Dieser Parameter gibt das Trennzeichen an, den der Host verwendet, das Skriptmodul zulassen, um eine bedingte, primitive Vorverarbeitung bereitzustellen, \(beispielsweise ein einfaches Anführungszeichen \['\] mit zwei einfache Anführungszeichen zur Verwendung als Trennzeichen\) ersetzt wird.  Genauer gesagt, wie \(und ob\) das Skriptmodul verwendet, sind diese Informationen im Skriptmodul ab.  Legen Sie diesen Parameter auf `NULL` fest, wenn der Host kein Trennzeichen verwendet, um das Ende der Prozedur zu markieren.  
  
 `dwSourceContextCookie`  
 \[in\] Anwendung festgelegten Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 \[in\] nullbasierter Wert, der angibt, welcher Zeile an die Analyse beginnt.  
  
 `dwFlags`  
 \[in\] Flags zugeordnete der Prozedur.  Kann eine Kombination dieser Werte.  
  
|Konstante|Wert|Bedeutung|  
|---------------|----------|---------------|  
|SCRIPTPROC\_ISEXPRESSION|0x00000020|Gibt an, dass der Code in `pstrCode` ein Ausdruck ist, der den Rückgabewert der Prozedur darstellt.|  
|SCRIPTPROC\_IMPLICIT\_THIS|0x00000100|Gibt an, dass der `this` Zeiger im Kontext der Prozedur enthalten ist.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|0x00000200|Gibt an, dass die übergeordneten Elemente des `this` Zeigers im Kontext der Prozedur enthalten sind.|  
  
 `ppdisp`  
 \[out\] Gibt einen Dispatchwrapper zurück, in dem die Standardmethode der Prozedur ist, die von analysiert wird.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt.  Das Skriptmodul unterstützt Ablaufeinführung von Prozeduren nicht auf den Namespace.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul im nicht initialisierten oder geschlossenen Zustand\).|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat in der Prozedur auf.|  
|`S_FALSE`|Das Skriptmodul unterstützt kein Dispatchobjekt; der `ppdisp`\-Parameter wird in `NULL` festgelegt.|  
  
## Hinweise  
 Kein Skriptcode wird während dieses Aufrufs ausgewertet, Sie wird die Prozedur in einer Methode für `ppdisp` kompiliert, in dem sie durch das Skript später aufgerufen werden kann.  
  
 Diese Schnittstelle wird zugunsten der `IActiveScriptParseProcedure`\-Schnittstelle veraltet.  Die `IActiveScriptParseProcedure::ParseProcedureText`\-Methode ist an diese Methode ähnlich, allerdings können den Prozedurnamen, angegeben werden.  unter allen Umständen sollte `IActiveScriptParseProcedure::ParseProcedureText` verwendet werden.  
  
## Siehe auch  
 [IActiveScriptParseProcedureOld\-Schnittstelle](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)