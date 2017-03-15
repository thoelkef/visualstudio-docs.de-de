---
title: "CA1500: Variablennamen sollten nicht mit Feldnamen &#252;bereinstimmen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VariableNamesShouldNotMatchFieldNames"
  - "CA1500"
helpviewer_keywords: 
  - "VariableNamesShouldNotMatchFieldNames"
  - "CA1500"
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1500: Variablennamen sollten nicht mit Feldnamen &#252;bereinstimmen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|Kategorie \(Category\)|Microsoft.Maintainability|  
|Unterbrechende Änderung|Wenn für einen Parameter ausgelöst, der über den gleichen Namen wie ein Feld verfügt:<br /><br /> -   Nicht unterbrechend – Wenn weder das Feld noch die Methode, durch die der Parameter deklariert wird, außerhalb der Assembly sichtbar sind, und zwar unabhängig von der vorgenommenen Änderung.<br />-   Unterbrechend – Wenn Sie den Feldnamen ändern und das Feld außerhalb der Assembly sichtbar ist.<br />-   Unterbrechend – Wenn Sie den Parameternamen ändern und die Methode, durch die er deklariert wird, außerhalb der Assembly sichtbar ist.<br /><br /> Wenn für eine lokale Variable ausgelöst, die den gleichen Namen wie ein Feld hat:<br /><br /> -   Nicht unterbrechend – Wenn das Feld außerhalb der Assembly nicht sichtbar ist, und zwar unabhängig von der vorgenommenen Änderung.<br />-   Nicht unterbrechend – Wenn Sie zwar den Namen der lokalen Variablen, nicht aber den Feldnamen ändern.<br />-   Unterbrechend – Wenn Sie den Feldnamen ändern und das Feld außerhalb der Assembly sichtbar ist.|  
  
## Ursache  
 Mit einer Instanzenmethode wird ein Parameter oder eine lokale Variable deklariert, dessen bzw. deren Name mit dem Namen eines Instanzenfelds des deklarierenden Typs übereinstimmt.  Um lokale Variablen, die gegen die Regel verstoßen, abzufangen, muss die getestete Assembly mit Debuginformationen erstellt werden, und die zugehörige Programmdatenbankdatei \(PDB\) muss verfügbar sein.  
  
## Regelbeschreibung  
 Wenn der Name eines Instanzenfelds mit dem Namen eines Parameters oder einer lokalen Variablen übereinstimmt, wird im Methodentext mit dem `this`\-Schlüsselwort \(`Me` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) auf das Instanzenfeld zugegriffen.  Bei der Codeverwaltung gerät dieser Unterschied leicht in Vergessenheit, und dann wird häufig angenommen, dass sich der Parameter bzw. die lokale Variable auf das Instanzenfeld bezieht, wodurch Fehler entstehen.  Dies gilt besonders für lange Methodentexte.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie entweder den Parameter\/die Variable oder das Feld um.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Verstöße gegen diese Regel veranschaulicht.  
  
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-cs[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]