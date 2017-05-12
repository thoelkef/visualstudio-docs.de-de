---
title: "IActiveScriptAuthor::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddTypeLib"
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptAuthor::AddTypeLib
Fügt eine Typbibliothek dem Namespace für das Skript hinzu.  
  
## Syntax  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### Parameter  
 `rguidTypeLib`  
 \[in\] Das Klassenbezeichner \(CLSID\) der Typbibliothek hinzugefügt werden.  
  
 `dwMajor`  
 \[in\] Die Hauptversionsnummer.  
  
 `dwMinor`  
 \[in\] Die Nebenversionsnummer.  
  
 `dwFlags`  
 \[in\] Wird nicht verwendet.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode ruft `LoadTypeLib`, um der Typbibliothek zu laden.  Nach dem Erfolg diesem Methodenaufrufe `IActiveScriptAuthor::AddNamedItem`, um von Typinformationen hinzuzufügen.  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/de-de/155b48e5-5438-409e-9342-630a6a500f60)