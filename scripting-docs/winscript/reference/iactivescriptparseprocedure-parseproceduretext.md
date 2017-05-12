---
title: "IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedure_ParseProcedureText"
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure::ParseProcedureText
Analysiert die angegebene Kennzahlprozedur und fügt die Prozedur dem Namespace hinzu.  
  
## Syntax  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### Parameter  
 `pstrCode`  
 \[in\] Adresse des Prozedurtexts auszuwerten.  Die Interpretation dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrFormalParams`  
 \[in\] Adresse von Namen des formalen Parameters für die Prozedur.  Die Parameternamen müssen mit den entsprechenden Trennzeichen für das Skriptmodul getrennt werden.  Die Namen dürfen nicht in Klammern eingeschlossen werden.  
  
 `pstrProcedureName`  
 \[in\] Adresse des zu verarbeitenden Prozedurnamens.  
  
 `pstrItemName`  
 \[in\] Adresse des Elementnamens, der den Kontext gibt, in der die Prozedur ausgewertet werden soll.  Wenn dieser Parameter `NULL` ist, wird der Code in den globalen Kontext des Skriptmoduls ausgewertet.  
  
 `punkContext`  
 \[in\] Adresse des Kontextobjekts.  Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solches Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen.  Wenn dieser Parameter `NULL` ist, verwendet das Modul `pstrItemName`, um den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 \[in\] Ende\-vonProzedur Adresse des Trennzeichens.  Wenn `pstrCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen, wie zwei einfache Anführungszeichen \("\), um das Ende der Prozedur zu erkennen.  Dieser Parameter gibt das Trennzeichen an, den der Host verwendet, das Skriptmodul zulassen, um eine bedingte Vorverarbeiten von Primitiva bereitzustellen, \(beispielsweise ein einfaches Anführungszeichen \['\] mit zwei einfachen Anführungszeichen zur Verwendung als Trennzeichen\) ersetzt wird.  Genauer gesagt, wie \(und ob\) das Skriptmodul ausnutzt, sind diese Informationen im Skriptmodul ab.  Legen Sie diesen Parameter auf `NULL` fest, wenn der Host kein Trennzeichen verwendet, um das Ende der Prozedur zu markieren.  
  
 `dwSourceContextCookie`  
 \[in\] Anwendung festgelegten Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 \[in\] beginnt nullbasierter Wert, der angibt, die die Analyse zeichnen, an.  
  
 `dwFlags`  
 \[in\] Flags zugeordnete der Prozedur.  Kann eine Kombination dieser Werte:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|SCRIPTPROC\_ISEXPRESSION|Gibt an, dass der Code in `pstrCode` ein Ausdruck ist, der den Rückgabewert der Prozedur darstellt.  Standardmäßig kann der Code einen Ausdruck, eine Liste von Anweisungen oder sonstige, die in einer Prozedur enthalten durch die Skriptsprache zugelassen werden.|  
|SCRIPTPROC\_IMPLICIT\_THIS|Gibt an, dass der `this` Zeiger im Kontext der Prozedur enthalten ist.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|Gibt an, dass die übergeordneten Elemente des `this` Zeigers im Kontext der Prozedur enthalten sind.|  
  
 `ppdisp`  
 \[out\] Adresse des Zeigers für das Objekt, das des globalen die Methoden und Eigenschaften Skripts enthält.  Wenn das Skriptmodul kein solches Objekt unterstützt, wird `NULL` zurückgegeben.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt.  Das Skriptmodul unterstützt Ablaufeinführung von Prozeduren nicht auf den Namespace.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul im nicht initialisierten oder geschlossenen Zustand\).|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat in der Prozedur auf.|  
|`S_FALSE`|Das Skriptmodul unterstützt kein Dispatchobjekt; der `ppdisp`\-Parameter wird in `NULL` festgelegt.|  
  
## Hinweise  
 Kein Skriptcode wird während dieses Aufrufs ausgewertet, Sie wird die Prozedur in den Skriptzustand kompiliert, in dem sie durch das Skript später aufgerufen werden kann.  
  
## Siehe auch  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)