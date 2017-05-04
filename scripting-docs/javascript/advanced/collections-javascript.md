---
title: "Auflistungen (JavaScript) | Microsoft Docs"
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
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Auflistungen (JavaScript)
Sie können die Auflistungsobjekte [Map](../../javascript/reference/map-object-javascript.md), [Set](../../javascript/reference/set-object-javascript.md) und [WeakMap](../../javascript/reference/weakmap-object-javascript.md) verwenden, um Werte und Objekte zu speichern.  Diese Objekte stellen einfache Methoden zum Hinzufügen und Abrufen von Member bereit, indem sie entweder einen Schlüssel oder einen Wert anstelle eines Index verwenden.  Um mithilfe eines Index auf Member einer Auflistung zuzugreifen, verwenden Sie stattdessen ein `Array`\-Objekt.  Weitere Informationen finden Sie unter [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md).  
  
> [!CAUTION]
>  `Map`, `Set` und `WeakMap` werden nicht in Browserversionen vor Internet Explorer 11. unterstützt.  Weitere Informationen zur Versionsunterstützung finden Sie unter [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
## Verwenden von Auflistungen  
 Die `Map` und `WeakMap`\-Objekte speichern Schlüssel\-Wert\-Paare und ermöglichen es Ihnen, durch Verwendung des Schlüssels Member hinzuzufügen, abzurufen und zu entfernen.  Der Schlüssel und der Wert kann von jedem beliebigen Typ sein.  Das `Set`\-Objekt speichert Werte beliebigen Typs.  
  
 Die `Map`\- und `Set`\-Objekte ermöglichen Ihnen das Aufzählen von Auflistungsmembern, indem die `forEach`\-Methode verwendet wird und die Überprüfung der Größe der Auflistung, indem die `size`\-Methode verwendet wird.  Das `WeakMap`\-Objekt ist dagegen nicht aufzählbar.  Für diese Auflistung werden die Schlüsselverweise schwach gehalten.  Verwenden Sie `WeakMap`, wenn der Garbage Collector bestimmen soll, ob die App jeden Member der Auflistung im Arbeitsspeicher beibehalten muss.  Das ist z. B. möglicherweise in Zwischenspeicherszenarien hilfreich, wo zwischengespeicherte Objekte sehr groß sind und Sie keine Objekte unnötig im Arbeitsspeicher halten möchten.  In einigen Szenarien können Sie dieses Objekt verwenden, um Speicherverluste zu verhindern.  
  
 Im folgenden Beispiel wird die Verwendung des `Map`\-Objekts gezeigt.  In diesem Beispiel können Sie auf Member zugreifen, indem Sie sowohl `get` als auch `forEach` verwenden.  Die Rückruffunktion in `forEach` kann bis zu drei Parameter annehmen, die den Wert des aktuellen Auflistungselements, den Schlüssel des aktuellen Elements und das Auflistungsobjekt selbst bereitstellen.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 Die Verwendung von `WeakMap` ist mit `Map` vergleichbar, außer dass Sie Member nur mithilfe von `get` abrufen können.  Ein Beispiel stellt das [WeakMap](../../javascript/reference/weakmap-object-javascript.md)\-Objekt dar.  
  
 Im folgenden Beispiel wird die Verwendung des `Set`\-Objekts gezeigt.  In diesem Beispiel nimmt die Rückruffunktion einen Parameter an, der der Wert des aktuellen Auswahlelements ist.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Siehe auch  
 [Erweitertes JavaScript](../../javascript/advanced/advanced-javascript.md)