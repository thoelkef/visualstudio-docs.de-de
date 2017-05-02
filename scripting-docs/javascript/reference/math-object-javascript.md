---
title: "Math-Objekt (JavaScript) | Microsoft Docs"
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
  - "Math-Objekt"
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Math-Objekt (JavaScript)
Ein systeminternes Objekt, das grundlegende mathematische Funktionen und Konstanten bietet.  
  
## Syntax  
  
```  
  
Math.[{property | method}]  
```  
  
## Parameter  
 *Eigenschaft*  
 Erforderlich.  Name einer der Eigenschaften des **Math** \-Objekts.  
  
 *Methode*  
 Erforderlich.  Name einer der Methoden des **Math** \-Objekts.  
  
## Hinweise  
 Das **Math**\-Objekt kann nicht mit dem Operator **new** erstellt werden; bei dessen Verwendung wird eine Fehlermeldung ausgegeben.  Wenn das Skriptmodul geladen ist, erstellt es das Objekt.  Alle seine Methoden und Eigenschaften sind jederzeit für das Skript verfügbar.  
  
## Anforderungen  
 Das `Math`\-Objekt wurde in [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] eingeführt.  
  
<a name="js56jsobjmathprop"></a>   
## Konstanten  
 In der folgenden Tabelle werden die Konstanten des `Math`\-Objekts aufgelistet.  
  
|Konstante|Beschreibung|  
|---------------|------------------|  
|[Math.E\-Konstante](../../javascript/reference/math-constants-javascript.md)|Die mathematische Konstante e.  Dies ist die eulersche Zahl, die Basis des natürlichen Logarithmus.|  
|[Math.LN2\-Konstante](../../javascript/reference/math-constants-javascript.md)|Der natürliche Logarithmus von 2.|  
|[Math.LN10\-Konstante](../../javascript/reference/math-constants-javascript.md)|Der natürliche Logarithmus von 10.|  
|[Math.LOG2E\-Konstante](../../javascript/reference/math-constants-javascript.md)|Der Logarithmus zur Basis 2 von e.|  
|[Math.LOG10E\-Konstante](../../javascript/reference/math-constants-javascript.md)|Der Logarithmus zur Basis 10 von e.|  
|[Math.PI\-Konstante](../../javascript/reference/math-constants-javascript.md)|Pi.  Dies ist das Verhältnis vom Umfang eines Kreises zu dessen Durchmesser.|  
|[Math.SQRT1\_2\-Konstante](../../javascript/reference/math-constants-javascript.md)|Die Quadratwurzel von 0,5 oder, anders ausgedrückt, 1 dividiert durch die Quadratwurzel von 2.|  
|[Math.SQRT2\-Konstante](../../javascript/reference/math-constants-javascript.md)|Die Quadratwurzel von 2.|  
  
<a name="js56jsobjmathmeth"></a>   
## Funktionen  
 In der folgenden Tabelle werden die Funktionen des `Math`\-Objekts aufgeführt.  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|[Math.abs\-Funktion](../../javascript/reference/math-abs-function-javascript.md)|Gibt den absoluten Wert einer Zahl zurück.|  
|[Math.acos\-Funktion](../../javascript/reference/math-acos-function-javascript.md)|Gibt den Arkuskosinus einer Zahl zurück.|  
|[Math.acosh\-Funktion](../../javascript/reference/math-acosh-function-javascript.md)|Gibt den hyperbolischen Arkuskosinus \(oder den umgekehrten hyperbolischen Kosinus\) einer Zahl zurück.|  
|[Math.asin\-Funktion](../../javascript/reference/math-asin-function-javascript.md)|Gibt den Arkussinus einer Zahl zurück.|  
|[Math.asinh\-Funktion](../../javascript/reference/math-asinh-function-javascript.md)|Gibt den umgekehrten Hyperbelsinus einer Zahl zurück.|  
|[Math.atan\-Funktion](../../javascript/reference/math-atan-function-javascript.md)|Gibt den Arkustangens einer Zahl zurück.|  
|[Math.atan2\-Funktion](../../javascript/reference/math-atan2-function-javascript.md)|Gibt den Winkel \(im Bogenmaß\) von der X\-Achse zu einem Punkt zurück, der durch die angegebenen X\- und Y\-Koordinaten dargestellt wird.|  
|[Math.atanh\-Funktion](../../javascript/reference/math-atanh-function-javascript.md)|Gibt den umgekehrten Hyperbeltangens einer Zahl zurück.|  
|[Math.ceil\-Funktion](../../javascript/reference/math-ceil-function-javascript.md)|Gibt die kleinste Ganzzahl zurück, die größer oder gleich dem angegebenen numerischen Ausdruck ist.|  
|[Math.cos\-Funktion](../../javascript/reference/math-cos-function-javascript.md)|Gibt den Kosinus einer Zahl zurück.|  
|[Math.cosh\-Funktion](../../javascript/reference/math-cosh-function-javascript.md)|Gibt den Hyperbelkosinus einer Zahl zurück.|  
|[Math.exp\-Funktion](../../javascript/reference/math-exp-function-javascript.md)|Gibt die potenzierte Konstante *e* \(die Basis des natürlichen Logarithmus\) zurück.|  
|[Math.expm1\-Funktion](../../javascript/reference/math-expm1-function-javascript.md)|Gibt die potenzierte Konstante e \(die Basis des natürlichen Logarithmus\) minus 1 zurück.|  
|[Math.floor\-Funktion](../../javascript/reference/math-floor-function-javascript.md)|Gibt die größte Ganzzahl zurück, die kleiner oder gleich dem angegebenen numerischen Ausdruck ist.|  
|[Math.hypot\-Funktion](../../javascript/reference/math-hypot-function-javascript.md)|Gibt die Quadratwurzel der Summe der Quadrate der Argumente zurück.|  
|[Math.imul\-Funktion](../../javascript/reference/math-imul-function-javascript.md)|Gibt das Produkt zweier Zahlen zurück, die als 32\-Bit\-Ganzzahlen mit Vorzeichen behandelt werden.|  
|[Math.log\-Funktion](../../javascript/reference/math-log-function-javascript.md)|Gibt den natürlichen Logarithmus einer Zahl zurück.|  
|[Math.log1p\-Funktion](../../javascript/reference/math-log1p-function-javascript.md)|Gibt den natürlichen Logarithmus von 1 \+ einer Zahl zurück.|  
|[Math.log10\-Funktion](../../javascript/reference/math-log10-function-javascript.md)|Gibt den Logarithmus einer Zahl zur Basis 10 zurück.|  
|[Math.log2\-Funktion](../../javascript/reference/math-log2-function-javascript.md)|Gibt den Logarithmus einer Zahl zur Basis 2 zurück.|  
|[Math.max\-Funktion](../../javascript/reference/math-max-function-javascript.md)|Gibt den größeren von zwei angegebenen numerischen Ausdrücken zurück.|  
|[Math.min\-Funktion](../../javascript/reference/math-min-function-javascript.md)|Gibt die kleinere von zwei angegebenen Zahlen zurück.|  
|[Math.pow\-Funktion](../../javascript/reference/math-pow-function-javascript.md)|Gibt den mit einer angegebenen Zahl potenzierten Wert eines Basisausdrucks zurück.|  
|[Math.random\-Funktion](../../javascript/reference/math-random-function-javascript.md)|Gibt eine Pseudozufallszahl zwischen 0 und 1 zurück.|  
|[Math.round\-Funktion](../../javascript/reference/math-round-function-javascript.md)|Gibt einen angegebenen numerischen Ausdruck auf die nächste Ganzzahl gerundet zurück.|  
|[Math.sign\-Funktion](../../javascript/reference/math-sign-function-javascript.md)|Gibt das Vorzeichen einer Zahl zurück und gibt damit an, ob die Zahl positiv, negativ oder 0 ist.|  
|[Math.sin\-Funktion](../../javascript/reference/math-sin-function-javascript.md)|Gibt den Sinus einer Zahl zurück.|  
|[Math.sinh\-Funktion](../../javascript/reference/math-sinh-function-javascript.md)|Gibt den umgekehrten Hyperbelsinus einer Zahl zurück.|  
|[Math.sqrt\-Funktion](../../javascript/reference/math-sqrt-function-javascript.md)|Gibt die Quadratwurzel einer Zahl zurück.|  
|[Math.tan\-Funktion](../../javascript/reference/math-tan-function-javascript.md)|Gibt den Tangens einer Zahl zurück.|  
|[Math.tanh\-Funktion](../../javascript/reference/math-tanh-function-javascript.md)|Gibt den Hyperbeltangens einer Zahl zurück.|  
|[Math.trunc\-Funktion](../../javascript/reference/math-trunc-function-javascript.md)|Gibt den ganzzahligen Teil einer Zahl ohne Nachkommastellen zurück.|  
  
## Siehe auch  
 [JavaScript\-Objekte](../../javascript/reference/javascript-objects.md)   
 [Number\-Objekt](../../javascript/reference/number-object-javascript.md)