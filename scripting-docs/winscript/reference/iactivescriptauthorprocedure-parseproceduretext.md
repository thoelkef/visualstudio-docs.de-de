---
title: "IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthorProcedure::ParseProcedureText"
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthorProcedure::ParseProcedureText
Analysiert eine Kennzahlprozedur, fügt den Text der Kennzahlprozedur dem Skripterstellungsmodul hinzu und erstellt ein `IScriptEntry`\-Objekt, das der Kennzahlprozedur entspricht.  
  
## Syntax  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### Parameter  
 `pszCode`  
 \[in\] Der analysieren Skripttext.  
  
 `pszFormalParams`  
 \[in\] Die Adresse der Namen des formalen Parameters für die Prozedur.  Die Parameternamen müssen durch die entsprechenden Trennzeichen für das Skripterstellungsmodul getrennt werden.  Die Namen dürfen nicht in die Klammern eingeschlossen werden.  
  
 `pszProcedureName`  
 \[in\] Die Adresse des zu verarbeitenden Prozedurnamens.  
  
 `pszItemName`  
 \[in\] Die Pufferadresse, die den Elementnamen enthält, der mit dem `IScriptEntry`\-Objekt zugeordnet ist.  
  
 `pszDelimiter`  
 \[in\] Die Adresse des Ende\-von\-SkriptBlock Trennzeichens.  Wenn `pszCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen \(wie zwei einfache Anführungszeichen\), um das Ende des Skriptblocks zu erkennen.  Legen Sie diesen Parameter auf fest, um auf NULL, wenn kein Trennzeichen gibt, zum Ende des Skriptblocks zu markieren.  
  
 `dwCookie`  
 \[in\] Ein Anwendung festgelegten Wert, der mit dem neuen `IScriptEntry`\-Objekt zugeordnet ist.  
  
 `dwFlags`  
 \[in\] Wird nicht verwendet.  
  
 `pdispFor`  
 \[in\] Wird nicht verwendet.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Das aktuelle [!INCLUDE[javascript](../../includes/javascript-md.md)] Modul implementiert diese Methode nicht.  
  
## Siehe auch  
 [IActiveScriptAuthorProcedure\-Schnittstelle](../../winscript/reference/iactivescriptauthorprocedure-interface.md)