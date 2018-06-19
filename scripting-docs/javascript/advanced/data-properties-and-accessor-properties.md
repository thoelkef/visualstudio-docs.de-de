---
title: Dateneigenschaften und Zugriffsmethodeneigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569470"
---
# <a name="data-properties-and-accessor-properties"></a>Dateneigenschaften und Zugriffsmethodeneigenschaften
In diesem Abschnitt finden Sie alle relevanten Informationen zu Dateneigenschaften und Zugriffsmethodeneigenschaften.  
  
### <a name="data-properties"></a>Dateneigenschaften  
 Eine *Dateneigenschaft* ist eine Eigenschaft, die einen Wert abrufen und festlegen kann. Dateneigenschaften enthalten die `value`- und `writable`-Eigenschaften in ihren Deskriptoren.  
  
 Die folgende Tabelle enthält die Attribute eines Dateneigenschaftendeskriptors.  
  
|Datendeskriptorattribut|Beschreibung|Standard|  
|-------------------------------|-----------------|-------------|  
|`value`|Der aktuelle Wert der Eigenschaft.|`undefined`|  
|`writable`|`true` oder `false`. Wenn für `writable` der Wert `true` festgelegt wird, kann der Eigenschaftswert verändert werden.|`false`|  
|`enumerable`|`true` oder `false`. Wenn für `enumerable` der Wert `true` festgelegt wird, kann die Eigenschaft durch eine `for...in`-Anweisung aufgelistet werden.|`false`|  
|`configurable`|`true` oder `false`. Wenn für `configurable` der Wert `true` festgelegt wird, können Eigenschaftenattribute verändert und die Eigenschaft gelöscht werden.|`false`|  
  
 Wenn der Deskriptor nicht über das `value`-, `writable`-, `get`- oder `set`-Attribut verfügt und der angegebene Eigenschaftenname nicht vorhanden ist, wird eine Dateneigenschaft hinzugefügt.  
  
 Wenn für das `configurable`-Attribut der Wert `false` und für `writable` der Wert `true` festgelegt ist, können die `value`- und `writable`-Attribute geändert werden.  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>Hinzufügen von Dateneigenschaften ohne defineProperty  
 Wenn Sie eine Dateneigenschaft hinzufügen und dabei nicht die `Object.defineProperty`-, `Object.defineProperties`- oder `Object.create`-Funktionen verwenden, wird für die `writable`-, `enumerable`- und `configurable`-Attribute der Wert `true` festgelegt. Nachdem Sie die Eigenschaft hinzugefügt haben, können Sie sie mit der `Object.defineProperty`-Funktion ändern.  
  
 Folgende Möglichkeiten stehen Ihnen zum Hinzufügen einer Dateneigenschaft zur Verfügung:  
  
-   Verwendung eines Zuweisungsoperators (=). Beispiel: `obj.color = "white";`  
  
-   Verwendung eines Objektliterals. Beispiel: `obj = { color: "white", height: 5 };`  
  
-   Verwendung einer Konstruktorfunktion, wie unter [Verwenden von Konstruktoren zum Definieren von Typen](../../javascript/advanced/using-constructors-to-define-types.md) beschrieben  
  
### <a name="accessor-properties"></a>Zugriffsmethodeneigenschaften  
 Eine *Zugriffsmethodeneigenschaft* ruft immer dann eine vom Benutzer bereitgestellte Funktion auf, wenn der Eigenschaftenwert festgelegt oder abgerufen wird. Der Deskriptor für eine Zugriffsmethodeneigenschaft enthält ein `get`-Attribut, ein `set`-Attribut oder beide Attribute.  
  
 Die folgende Tabelle enthält die Attribute eines Deskriptors für Zugriffsmethodeneigenschaften.  
  
|Attribut für Zugriffsmethodendeskriptor|Beschreibung|Standard|  
|-----------------------------------|-----------------|-------------|  
|`get`|Eine Funktion, die den Eigenschaftenwert zurückgibt. Die Funktion hat keine Parameter.|`undefined`|  
|`set`|Eine Funktion, die den Eigenschaftenwert festlegt. Sie verfügt über einen Parameter, der den Wert enthält, der zugewiesen werden soll.|`undefined`|  
|`enumerable`|`true` oder `false`. Wenn für `enumerable` der Wert `true` festgelegt wird, kann die Eigenschaft durch eine `for...in`-Anweisung aufgelistet werden.|`false`|  
|`configurable`|`true` oder `false`. Wenn für `configurable` der Wert `true` festgelegt wird, können Eigenschaftenattribute verändert und die Eigenschaft gelöscht werden.|`false`|  
  
 Wenn eine `get`-Zugriffsmethode nicht definiert ist und der Versuch unternommen wird, auf den Eigenschaftswert zuzugreifen, wird der Wert `undefined` zurückgegeben. Wenn eine `set`-Zugriffsmethode nicht definiert ist und der Versuch unternommen wird, der Zugriffsmethodeneigenschaft einen Wert zuzuweisen, geschieht nichts.  
  
### <a name="property-modifications"></a>Eigenschaftenänderungen  
 Wenn das Objekt bereits über eine Eigenschaft mit dem angegebenen Namen verfügt, werden die Eigenschaftenattribute geändert. Wenn Sie die Eigenschaft ändern, bleiben Attribute, die nicht im Deskriptor angegeben sind, unverändert.  
  
 Wenn dem `configurable`-Attribut einer vorhandenen Eigenschaft der Wert `false` zugewiesen wurde, darf nur das `writable`-Attribut von `true` zu `false` geändert werden.  
  
 Sie können eine Dateneigenschaft in eine Zugriffsmethodeneigenschaft umwandeln und umgekehrt. In diesem Fall werden nicht im Deskriptor angegebene `configurable`- und `enumerable`-Attribute in der Eigenschaft beibehalten. Anderen Attributen, die nicht im Deskriptor angegeben sind, werden die jeweiligen Standardwerte zugewiesen.  
  
 Sie können konfigurierbare Zugriffsmethodeneigenschaften inkrementell erstellen, indem Sie die `Object.defineProperty`-Funktion mehrfach aufrufen. So kann z.B. durch den ersten Aufruf von `Object.defineProperty` nur eine `get`-Zugriffsmethode definiert werden. Durch einen weiteren Aufruf des gleichen Eigenschaftsnamens kann anschließend eine `set`-Zugriffsmethode definiert werden. Die Eigenschaft besitzt dann sowohl eine `get`- als auch eine `set`-Zugriffsmethode.  
  
 Um ein Deskriptorobjekt zu erhalten, das auf eine vorhandene Eigenschaft angewendet wird, können Sie die [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) verwenden.  
  
 Sie können die [Object.seal-Funktion](../../javascript/reference/object-seal-function-javascript.md) und die [Object.freeze-Funktion](../../javascript/reference/object-freeze-function-javascript.md) verwenden, um Änderungen an Eigenschaftenattributen zu verhindern.