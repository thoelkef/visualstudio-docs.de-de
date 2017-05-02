---
title: "Debugobjekt (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "debug"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Debugobjekt"
  - "Debugobjekt, über das Debugobjekt"
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Debugobjekt (JavaScript)
Ein systeminternes globales Objekt, das die Ausgabe an einen Debugger sendet.  
  
## Syntax  
  
```  
Debug.function  
```  
  
## Hinweise  
 Das Debug\-Objekt wird nicht instanziiert. Sie können auf alle zugehörigen Eigenschaften und Methoden zugreifen, indem Sie `function` aufrufen.  
  
 Es gibt verschiedene Möglichkeiten, Internet Explorer\- und [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps zu debuggen. In [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps zeigen die `write`\- und `writeln`\-Funktionen des `Debug`\-Objekte Zeichenfolgen zur Laufzeit im Visual Studio\-Fenster **Ausgabe** an. Weitere Informationen über das Debuggen von [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps finden Sie unter [Debuggen von Apps in Visual Studio](../Topic/Debug%20Store%20apps%20in%20Visual%20Studio.md).  
  
 Zum Debuggen von Internet Explorer\-Skripts, muss ein Skriptdebugger installiert sein, und das Skript muss im Debugmodus ausgeführt werden. Internet Explorer 8 und neuere Versionen enthalten den [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Debugger. Wenn Sie eine frühere Version von Internet Explorer verwenden, finden Sie unter [Gewusst wie: Aktivieren und Starten des Skriptdebuggings in Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801) weitere Informationen.  
  
 Wenn das Skript nicht debuggt wird, haben die Funktionen keine Auswirkungen.  
  
## Beispiel  
 In diesem Beispiel wird die `write`\-Funktion verwendet, um den Wert der Variablen anzuzeigen.  
  
```javascript  
var counter = 42; Debug.write("The value of counter is " + counter);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Konstanten  
 [Debug\-Konstanten](../../javascript/reference/debug-constants.md)  
  
## Eigenschaften  
 [Debug.debuggerEnabled\-Eigenschaft](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setNonUserCodeExceptions\-Eigenschaft](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## Funktionen  
 [Debug.msTraceAsyncCallbackStarting\-Funktion](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Debug.msTraceAsyncCallbackCompleted\-Funktion](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Debug.msTraceAsyncOperationCompleted\-Funktion](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Debug.msTraceAsyncOperationStarting\-Funktion](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Debug.msUpdateAsyncCallbackRelation\-Funktion](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.write\-Funktion](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln\-Funktion](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## Siehe auch  
 [debugger\-Anweisung](../../javascript/reference/debugger-statement-javascript.md)