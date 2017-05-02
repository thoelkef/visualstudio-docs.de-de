---
title: "Boolean-Objekt (JavaScript) | Microsoft Docs"
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
  - "boolean_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Boolean-Datentyp, Boolean-Objekt"
  - "Boolean-Objekt"
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Boolean-Objekt (JavaScript)
Erstellt einen neuen booleschen Wert.  
  
## Syntax  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## Parameter  
 `boolObj`  
 Erforderlich.  Der Variablenname, dem das `Boolean`\-Objekt zugewiesen wird.  
  
 `boolValue`  
 Optional.  Der anfängliche Boolesche Wert des neuen Objekts.  Ist `boolvalue` nicht vorhanden oder `false`, 0, `null`, `NaN` oder eine leere Zeichenfolge, ist der anfängliche Wert des Boolean\-Objekts `false`.  Andernfalls ist der anfängliche Wert `true`.  
  
## Hinweise  
 Das `Boolean`\-Objekt ist ein Wrapper für den Booleschen Datentyp.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet implizit das `Boolean`\-Objekt, wenn ein Boolescher Datentyp in ein `Boolean`\-Objekt konvertiert wird.  
  
 Das `Boolean`\-Objekt wird selten explizit instanziiert.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Boolean`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[constructor\-Eigenschaft](../../javascript/reference/constructor-property-boolean.md)|Gibt die Funktion an, mit der ein Boolean\-Objekt erstellt wird.|  
|[prototype\-Eigenschaft](../../javascript/reference/prototype-property-boolean.md)|Gibt einen Verweis auf den Prototyp einen Booleschen Wert zurück.|  
  
<a name="js56jsobjarraymeth"></a>   
## Methoden  
 In der folgenden Tabelle werden die Methoden des `Boolean`\-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[toString\-Methode](../../javascript/reference/tostring-method-boolean-1.md)|Gibt eine Zeichenfolgendarstellung eines Boolean\-Objekts zurück.|  
|[valueOf\-Methode](../../javascript/reference/valueof-method-boolean.md)|Ruft einen Verweis auf das Boolean\-Objekt ab.|  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]