---
title: "Dateneigenschaften und Accessor-Eigenschaften | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Dateneigenschaften und Accessor-Eigenschaften
Dieser Abschnitt enthält alle Informationen, die Sie wahrscheinlich zu Dateneigenschaften und Accessoreigenschaften benötigen.  
  
### Dateneigenschaften  
 Eine *Dateneigenschaft* ist eine Eigenschaft, die einen Wert abrufen und festlegen kann.  Dateneigenschaften enthalten in ihren Deskriptoren die `value`\-Eigenschaft und die `writable`\-Eigenschaft.  
  
 In der folgenden Tabelle werden die Attribute eines Dateneigenschaftendeskriptors aufgeführt.  
  
|Datendeskriptorattribut|Beschreibung|Standardwert|  
|-----------------------------|------------------|------------------|  
|`value`|Der aktuelle Wert der Eigenschaft.|`undefined`|  
|`writable`|`true` oder `false`.  Wenn `writable` auf `true` festgelegt ist, kann der Eigenschaftswert geändert werden.|`false`|  
|`enumerable`|`true` oder `false`.  Wenn `enumerable` auf `true` festgelegt ist, kann die Eigenschaft durch eine `for…in`\-Anweisung aufgelistet werden.|`false`|  
|`configurable`|`true` oder `false`.  Wenn `configurable` auf `true` festgelegt ist, können Eigenschaftenattribute geändert werden, und die Eigenschaft kann gelöscht werden.|`false`|  
  
 Wenn der Deskriptor nicht über das Attribut `value`, `writable`, `get` oder `set` verfügt und der angegebene Eigenschaftenname nicht vorhanden ist, wird eine Dateneigenschaft hinzugefügt.  
  
 Wenn das `configurable`\-Attribut `false` und das `writable`\-Attribut `true` ist, können die Attribute `value` und `writable` geändert werden.  
  
#### Hinzufügen von Dateneigenschaften, ohne defineProperty zu verwenden  
 Wenn Sie eine Dateneigenschaft hinzufügen, ohne die Funktionen `Object.defineProperty`, `Object.defineProperties` oder `Object.create` zu verwenden, dann müssen die Attribute `writable`, `enumerable` und `configurable` alle auf `true` festgelegt werden.  Nachdem die Eigenschaft hinzugefügt worden ist, können Sie dies mithilfe der `Object.defineProperty`\-Funktion ändern.  
  
 Sie können die folgenden Methoden zum Hinzufügen einer Dateneigenschaft verwenden:  
  
-   Zuweisungsoperator \(\=\), wie in `obj.color = "white";`  
  
-   Objektliteral, wie in `obj = { color: "white", height: 5 };`  
  
-   Konstruktionsfunktion, wie in [Verwenden von Konstruktoren zum Definieren von Typen](../../javascript/advanced/using-constructors-to-define-types.md) beschrieben  
  
### Accessoreigenschaften  
 Eine *Accessoreigenschaft* ruft eine vom Benutzer bereitgestellte Funktion immer dann auf, wenn der Eigenschaftswert festgelegt oder abgerufen wird.  Der Deskriptor einer Accessoreigenschaft enthält ein `get`\-Attribut, ein `set`\-Attribut oder beides.  
  
 In der folgenden Tabelle werden die Attribute eines Accessoreigenschaftendeskriptors aufgeführt.  
  
|Accessordeskriptorattribut|Beschreibung|Standardwert|  
|--------------------------------|------------------|------------------|  
|`get`|Eine Funktion, die den Eigenschaftswert zurückgibt.  Die Funktion hat keine Parameter.|`undefined`|  
|`set`|Eine Funktion, die den Eigenschaftswert festlegt.  Sie enthält einen Parameter, der den zuzuweisenden Wert enthält.|`undefined`|  
|`enumerable`|`true` oder `false`.  Wenn `enumerable` auf `true` festgelegt ist, kann die Eigenschaft durch eine `for…in`\-Anweisung aufgelistet werden.|`false`|  
|`configurable`|`true` oder `false`.  Wenn `configurable` auf `true` festgelegt ist, können Eigenschaftenattribute geändert werden, und die Eigenschaft kann gelöscht werden.|`false`|  
  
 Wenn ein `get`\-Accessor nicht definiert ist und versucht wird, auf den Eigenschaftswert zuzugreifen, wird der Wert `undefined` zurückgegeben.  Wenn ein `set`\-Accessor nicht definiert ist und versucht wird, der Accessoreigenschaft einen Wert zuzuweisen, dann geschieht nichts.  
  
### Eigenschaftsänderungen  
 Wenn das Objekt bereits eine Eigenschaft mit dem angegebenen Namen besitzt, werden die Eigenschaftenattribute geändert.  Wenn Sie die Eigenschaft ändern, bleiben Attribute, die nicht im Deskriptor angegeben werden, unverändert.  
  
 Wenn das `configurable`\-Attribut einer vorhandenen Eigenschaft `false` ist, besteht die einzige zulässige Änderung darin, das `writable`\-Attribut von `true` in `false` zu ändern.  
  
 Sie können eine Dateneigenschaft in eine Accessoreigenschaft ändern und umgekehrt.  Wenn Sie dies tun, werden die Attribute `configurable` und `enumerable`, die nicht im Deskriptor angegeben sind, in der Eigenschaft beibehalten.  Andere Attribute, die nicht im Deskriptor angegeben sind, werden auf ihre Standardwerte festgelegt.  
  
 Sie können konfigurierbare Accessoreigenschaften inkrementell definieren, indem Sie die `Object.defineProperty`\-Funktion mehrmals aufrufen.  Beispielsweise könnte ein `Object.defineProperty` Aufruf nur einen `get` Accessor definieren.  Ein weiterer Aufruf für denselben Eigenschaftennamen definiert möglicherweise einen `set`\-Accessor.  Die Eigenschaft würde dann sowohl einen `get`\-Accessor als auch einen `set`\-Accessor besitzen.  
  
 Um ein Deskriptorobjekt zu erhalten, das für eine vorhandene Eigenschaft gilt, können Sie [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) verwenden.  
  
 Sie können [Object.seal\-Funktion](../../javascript/reference/object-seal-function-javascript.md) und [Object.freeze\-Funktion](../../javascript/reference/object-freeze-function-javascript.md) verwenden, um die Änderung von Eigenschaftattributen zu verhindern.