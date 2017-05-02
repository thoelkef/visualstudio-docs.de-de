---
title: "WinRTError-Objekt (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, WinRTError-Objekt"
  - "WinRTError-Objekt [JavaScript]"
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WinRTError-Objekt (JavaScript)
Wenn ein Windows\-Runtime\-Aufruf ein HRESULT zurückgibt, das einen Fehler angibt, wird dieser von JavaScript in einen speziellen Windows\-Runtime\-Fehler konvertiert.  Diese Funktion steht nur in [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-Apps zur Verfügung, wenn die Windows\-Runtime verfügbar ist \(als Teil des globalen JavaScript\-Namespace\).  
  
## Syntax  
  
```  
  
errorObj = new WinRTError();   
```  
  
## Hinweise  
 Der WinRTError\-Fehlertyp wird nur für Fehler verwendet, deren Ursprung in Windows\-Runtime\-APIs liegt.  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie ein WinRTError ausgelöst und abgefangen wird.  
  
```javascript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## Methoden  
 Das WinRTError\-Objekt hat keine Methoden.  
  
## Eigenschaften  
 Das WinRTError\-Objekt hat die gleichen Eigenschaften wie das [Error\-Objekt](../../javascript/reference/error-object-javascript.md)\-Objekt.  
  
## Anforderungen  
 Das WinRTError\-Objekt wird nur in [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-Apps unterstützt, nicht jedoch in Internet Explorer.  
  
## Siehe auch  
 [Error\-Objekt](../../javascript/reference/error-object-javascript.md)