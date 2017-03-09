---
title: "JavaScript Console commands | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "JavaScript-Konsolenbefehle [Windows Store-Apps]"
  - "JavaScript-Debugging, Konsole [Windows Store-Apps]"
  - "JavaScript debuggen, Konsole [Windows Store-Apps]"
ms.assetid: 359e2b24-6bb7-48e7-8b55-b570df0cb774
caps.latest.revision: 47
caps.handback.revision: 47
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JavaScript Console commands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Gilt für Windows und Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Sie können Befehle verwenden, um Nachrichten zu senden und weitere Aufgaben im JavaScript-Konsolenfenster von Visual Studio auszuführen. Beispiele zur Verwendung dieses Fensters finden Sie unter [Schnellstart: Debuggen von JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md). Die Informationen in diesem Thema beziehen sich auf Windows Store-Apps, Windows Phone Store-Apps und Apps, die mit Visual Studio-Tools für Apache Cordova erstellt wurden. Informationen zu unterstützten Konsolenbefehlen in Cordova-Apps finden Sie unter [Debug Your App](../Topic/Debug%20Your%20App%20Built%20with%20Visual%20Studio%20Tools%20for%20Apache%20Cordova.md). Informationen zur Verwendung der Konsole in Internet Explorer F12-Tools finden Sie in [diesem Thema](http://msdn.microsoft.com/library/ie/dn255006.aspx).  
  
 Wenn das JavaScript-Konsolenfenster geschlossen ist, können Sie es während des Debuggengens in Visual Studio öffnen, indem Sie auf **Debuggen** > **Windows** > **JavaScript-Konsole**.  
  
> [!NOTE]
>  Wenn das Fenster während einer Debugsitzung nicht verfügbar ist, stellen Sie sicher, dass der Debuggertyp in den Debugeigenschaften für das Projekt auf **Script** festgelegt ist.  
  
## <a name="console-object-commands"></a>Konsolenobjektbefehle  
 Diese Tabelle zeigt die Syntax für `console` -Objektbefehle, die Sie im JavaScript-Konsolenfenster oder zum Senden von Meldungen aus dem Code an die Konsole verwenden können. Dieses Objekt stellt mehrere Formulare bereit, damit Sie nach Bedarf zwischen Informationsmeldungen und Fehlermeldungen unterscheiden können.  
  
 Sie können die längere Befehlsform `window.console.[command]` verwenden, wenn Sie Verwechslungen mit lokalen console-Objekten vermeiden müssen.  
  
> [!TIP]
>  Ältere Versionen von Visual Studio unterstützen nicht den vollständigen Satz von Befehlen. Wenden Sie IntelliSense auf das Console-Objekt an, um schnell Informationen zu unterstützten Befehle zu erhalten.  
  
|Befehl|Beschreibung|Beispiel|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Sendet eine Meldung, wenn `expression` als **false**ausgewertet wird.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Löscht Skriptcode und Meldungen aus dem Konsolenfenster, einschließlich Skriptfehlermeldungen. Löscht keinen Skriptcode, den Sie in die Konsoleneingabeaufforderung eingegeben haben.|`console.clear();`|  
|`count(title)`|Sendet die Häufigkeit, mit der der count-Befehl im Konsolenfenster aufgerufen wurde. Jeder zu zählende Aufruf wird eindeutig durch optionale `title`identifiziert.<br /><br /> Der vorhandene Eintrag im Konsolenfenster wird durch den `title` -Parameter (falls vorhanden) identifiziert und durch den count-Befehl aktualisiert. Ein neuer Eintrag wird nicht erstellt.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Sendet `message` an das Konsolenfenster.<br /><br /> Dieser Befehl ist in console.log identisch.<br /><br /> Objekte, die mit dem Befehl übergeben werden, werden in einen Zeichenfolgenwert konvertiert.|`console.debug("logging message");`|  
|`dir(object)`|Sendet das angegebene Objekt an das Konsolenfenster und zeigt es in einer Objektschnellansicht an. Sie können die Schnellansicht verwenden, um Eigenschaften im Konsolenfenster zu überprüfen.|`console.dir(obj);`|  
|`dirxml(object)`|Sendet den angegebenen XML-Knoten `object` an das Konsolenfenster und zeigt ihn als XML-Knotenstruktur an.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Sendet `message` an das Konsolenfenster. Der Meldungstext ist rot, und ein Fehlersymbol wird vorangestellt.<br /><br /> Objekte, die mit dem Befehl übergeben werden, werden in einen Zeichenfolgenwert konvertiert.|`console.error("error message");`|  
|`group(title)`|Startet eine Gruppierung für Meldungen, die an das Konsolenfenster gesendet werden, und sendet optionale `title` während eine Gruppenbezeichnung. Gruppen können geschachtelt sein und in einer Strukturansicht im Konsolenfenster angezeigt werden.<br /><br /> In einigen Szenarien, z. B. wenn ein Komponentenmodell verwendet wird, können die group*-Befehle die Ausgabenanzeige im Konsolenfenster vereinfachen.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Startet eine Gruppierung für Meldungen, die an das Konsolenfenster gesendet werden, und sendet optionale `title` während eine Gruppenbezeichnung. Gruppen, die mit `groupCollapsed` gesendet werden, werden standardmäßig in einer reduzierten Ansicht angezeigt. Gruppen können geschachtelt sein und in einer Strukturansicht im Konsolenfenster angezeigt werden.|Die Verwendung ist identisch mit dem `group` -Befehl.<br /><br /> Siehe Beispiel für den `group` -Befehl.|  
|`groupEnd()`|Beendet die aktuelle Gruppe.<br /><br /> Anforderungen:<br /><br /> Visual Studio 2013|Siehe Beispiel für den `group` -Befehl.|  
|`info(message)`|Sendet `message` an das Konsolenfenster. Der Meldung wird ein Informationssymbol vorangestellt.|`console.info("info message");`<br /><br /> Weitere Beispiele finden Sie unter [Formatting console.log output](#ConsoleLog) weiter unten in diesem Thema.|  
|`log(message)`|Sendet `message` an das Konsolenfenster.<br /><br /> Wenn Sie ein Objekt übergeben, sendet der Befehl dieses Objekt an das Konsolenfenster und zeigt es in einer Objektschnellansicht an. Sie können die Schnellansicht verwenden, um Eigenschaften im Konsolenfenster zu überprüfen.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Wird in Web-Apps verwendet. Wird in Store-Apps mit JavaScript nicht unterstützt.|Wird nicht unterstützt.|  
|`profile(reportName)`|Wird in Web-Apps verwendet. Wird in Store-Apps mit JavaScript nicht unterstützt.|Wird nicht unterstützt.|  
|`profileEnd()`|Wird in Web-Apps verwendet. Wird in Store-Apps mit JavaScript nicht unterstützt.|Wird nicht unterstützt.|  
|`select(element)`|Wählt das angegebene HTML- `element` im [DOM Explorer](../debugger/quickstart-debug-html-and-css.md)aus.|console.select(element);|  
|`time (name)`|Startet einen Zeitgeber, der durch den optionalen Parameter `name` identifiziert wird. Wenn dieser Befehl mit `console.timeEnd`verwendet wird, wird die Zeit, die zwischen `time` und `timeEnd`verstreicht, berechnet, und das Ergebnis (gemessen in ms) wird mit der Zeichenfolge `name` als Präfix an die Konsole gesendet. Wird verwendet, um Instrumentation von App-Codes zum Messen der Leistung zu aktivieren.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|Stoppt einen Zeitgeber, der durch den optionalen Parameter `name` identifiziert wird. Siehe den Konsolenbefehl `time` .|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Sendet eine Stapelverfolgung an das Konsolenfenster. Die Ablaufverfolgung umfasst die vollständige Aufrufliste, z. B. Dateiname, Zeilennummer und Spaltennummer.|`console.trace();`|  
|`warn(message)`|Sendet `message` an das Konsolenfenster mit vorausgehendem Warnsymbol.<br /><br /> Objekte, die mit dem Befehl übergeben werden, werden in einen Zeichenfolgenwert konvertiert.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Verschiedene Befehle  
 Diese Befehle stehen auch im JavaScript-Konsolenfenster zur Verfügung (sie sind im Code nicht verfügbar).  
  
|Befehl|Beschreibung|Beispiel|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Gibt das angegebene Element im Konsolenfenster zurück. `$0` gibt das Element zurück, das gegenwärtig in DOM Explorer ausgewählt ist. `$1` gibt das Element zurück, das zuvor in DOM Explorer ausgewählt wurde usw., bis zum vierten zuvor ausgewählten Element.|$3|  
|`$(id)`|Gibt ein Element anhand der ID zurück. Dies ist ein Kurzbefehl für `document.getElementById(id)`, wobei `id` eine Zeichenfolge ist, die die Element-ID darstellt.|`$("contenthost")`|  
|`$$(selector)`|Gibt ein Array von Elementen, die dem angegebenen Selektor entsprechen, mithilfe der CSS-Selektor-Syntax zurück. Dies ist ein Kurzbefehl für `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|Ermöglicht es Ihnen, den Kontext für Ausdrucksauswertung vom Standardfenster der obersten Ebene der Seite in das Fenster des angegebenen Rahmens zu ändern. Ein Aufruf von `cd()` ohne Parameter gibt den Kontext zum Fenster der obersten Ebene zurück.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Wählt das angegebene Element im [DOM Explorer](../debugger/quickstart-debug-html-and-css.md)aus.|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Gibt eine Schnellansicht für das angegebene Objekt zurück. Sie können die Schnellansicht verwenden, um Eigenschaften im Konsolenfenster zu überprüfen.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Überprüfen des Vorhandenseins eines Konsolenbefehls  
 Sie können überprüfen, ob ein bestimmter Befehl vorhanden ist, bevor Sie versuchen ihn anzuwenden. In diesem Beispiel wird das Vorhandensein des Befehls `console.log` überprüft. Wenn `console.log` vorhanden ist, ruft der Code diesen Befehl auf.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>Überprüfen von Objekten im JavaScript-Konsolenfenster  
 Über das JavaScript-Konsolenfenster können Sie mit jedem Objekt interagieren, das im Bereich enthalten ist. Um ein Objekt, das außerhalb des gültigen Bereichs liegt, im Konsolenfenster zu überprüfen, führen Sie `console.log` , `console.dir`oder andere Befehle aus dem Code aus. Alternativ können Sie aus dem Konsolenfenster mit dem Objekt interagieren, während es innerhalb des gültigen Bereichs liegt. Dazu müssen Sie einen Haltepunkt im Code festlegen (**Haltepunkt** > **Insert Haltepunkt**.)  
  
##  <a name="a-nameconsoleloga-formatting-consolelog-output"></a><a name="ConsoleLog"></a> Formatieren der console.log-Ausgabe  
 Wenn Sie mehrere Argumente an `console.log`übergeben, behandelt die Konsole die Argumente als Array und verkettet die Ausgabe.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 `console.log` unterstützt auch „printf“-Ersetzungsmuster zum Formatieren der Ausgabe. Wenn Sie Ersetzungsmuster im ersten Argument verwenden, werden zusätzliche Argumente verwendet, um die angegebenen Muster in der Reihenfolge ihrer Verwendung zu ersetzen.  
  
 Die folgenden Ersetzungsmuster werden unterstützt:  
  
-   %s – Zeichenfolge  
     %i – Ganzzahl  
     %d – Ganzzahl  
     %f – Gleitkommazahl  
     %o – Objekt  
     %b – Binärzahl  
     %x – Hexadezimalzahl  
     %e – Exponent  
  
 Nachfolgend finden Sie einige Beispiele für die Verwendung von Ersetzungsmustern in `console.log`:  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
user.age = 10.01;  
console.log("Hi, %s %s!", user.first, user.last);  
console.log("%s is %i years old!", user.first, user.age);  
console.log("%s is %f years old!", user.first, user.age);  
  
// Output:  
// Hi, Fred Smith!  
// Fred is 10 years old!  
// Fred is 10.01 years old!  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schnellstart: Debuggen von JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)