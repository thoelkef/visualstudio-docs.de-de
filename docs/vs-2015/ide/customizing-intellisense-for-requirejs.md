---
title: Anpassen von IntelliSense für RequireJS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7b1c32d0096742c2364e5ac3b8afe59b39152b2b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246713"
---
# <a name="customizing-intellisense-for-requirejs"></a>Anpassen von IntelliSense für RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beginnend mit Visual Studio 2013 Update 4 wird Unterstützung für die beliebte RequireJS-JavaScript-Datei und das modulare Ladeprogramm unterstützt. RequireJS erleichtert das Definieren von Abhängigkeiten zwischen Codemodulen und das dynamische Laden von Modulen nur bei Bedarf. Beim Schreiben von JavaScript-Code, der RequireJS verwendet, werden IntelliSense Vorschläge für Module bereitgestellt, auf die Sie aus Ihrer Moduldefinition verwiesen oder mit Aufrufen von `require()` aus dem Code heraus verwiesen haben.  
  
 Visual Studio unterstützt standardmäßig eine sehr einfache Konfiguration zur Unterstützung von RequireJS, aber es ist üblich, dass Sie Ihre eigenen benutzerdefinierten Konfigurationseinstellungen einrichten (das heißt, Aliase für Bibliotheken definieren). Dieses Thema beschreibt die verschiedenen Möglichkeiten, über die Sie Visual Studio so anpassen können, dass es mit der einzigartigen Einrichtung Ihres Projekts funktioniert.  
  
 In diesem Thema wird Folgendes erläutert:  
  
-   Anpassen von RequireJS in ASP.NET-Projekten  
  
-   Anpassen von RequireJS in JSProj-Projekten, die verwendet werden, um Apache Cordova-apps, Windows Store-Apps und LightSwitch-HTML-Apps zu erstellen.  
  
## <a name="customize-requirejs-in-aspnet-projects"></a>Anpassen von RequireJS in ASP.NET-Projekten  
 Unterstützung für RequireJS wird automatisch aktiviert, wenn eine Datei mit dem Namen "Require.js" durch Ihre aktuelle JavaScript-Datei verwiesen wird (Weitere Informationen finden Sie im Abschnitt "Bestimmen des IntelliSense-Kontexts" in [JavaScript IntelliSense](../ide/javascript-intellisense.md)). In ASP.NET-Projekten, verweisen auf "Require.js" erfolgt in der Regel mit einer / / / \<Reference / >-Anweisung in einer _references.js-Datei.  
  
### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Konfigurieren des Data-Main-Attributs in einem ASP.NET-Projekt  
 Um korrekt zu simulieren, wie Ihre App bei Ausführung funktioniert, muss der JavaScript-Editor wissen, welche Datei zuerst geladen werden soll, wenn Sie "require.js" einrichten. Dies wird in der Regel in der Anwendungs-HTML-Datei mit dem `data-main`-Attribut für das Script-Element konfiguriert, das auf "require.js" verweist, wie nachfolgend dargestellt.  
  
```html  
<script src="js/require.js" data-main="js/app.js"></script>  
```  
  
 In diesem Beispiel wird das Skript, auf das von data-main (js/app.js) verwiesen wird, unmittelbar nach "require.js" geladen. Die Datei, die sofort geladen wird, ist der beste Ort zum Konfigurieren Sie zuerst die RequireJS-Nutzung (mit `require.config()`). Um JavaScript-Editor mitzuteilen, welche Datei für die Verwendung `data-main` in Ihrer Anwendung Hinzufügen einer `data-main` Attribut, und ändern Sie dann eine / / / \<Reference / > Richtlinie, die auf "Require.js" in Ihrer Anwendung verweist. Sie können diese Anweisung beispielsweise für Folgendes verwenden:  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" />  
```  
  
### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Konfigurieren der Startseite der Anwendung in einem ASP.NET-Projekt  
 Wenn die app ausgeführt wird, RequireJS setzt voraus, dass relative Pfade zu Dateien (z. B. "... \\"Pfade) sind relativ zur HTML-Datei, die die Bibliothek" Require.js "geladen. Beim Schreiben von Code im Visual Studio-Editor für ein ASP.NET-Projekt, ist diese Startseite unbekannt, und Sie müssen dem Editor mitteilen, welche Startseite verwendet werden soll, wenn Sie relative Dateipfade verwenden. Zu diesem Zweck fügen eine `start-page` -Attribut auf der / / / \<Reference / > Richtlinie.  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />  
```  
  
 Das `start-page`-Attribut gibt die URL der Seite an, wie sie in einem Browser beim Ausführen der App angezeigt würde.  
  
## <a name="customize-requirejs-in-jsproj-projects"></a>Anpassen von RequireJS in JSProj-Projekten  
 Beim Erstellen von Apps für Apache Cordova, HTML-basierte Windows Store-Apps oder LightSwitch-HTML-Apps werden JSProj-Projekte (Projektdateien mit der Erweiterung ".jsproj") verwendet. Im Gegensatz zu ASP.NET-Projekten lesen diese Projekte Verweise auf die JS-Dateien aus HTML-Dateien, die im Projekt vorhanden sind. Aus diesem Grund wird beim Bearbeiten von JavaScript in einem Projekt JSProj Unterstützung für RequireJS aktiviert, wenn auf die JavaScript-Datei, die derzeit bearbeitet wird, in einer anderen HTML-Datei verwiesen wird, die auch auf "require.js" verweist.  
  
 Die Anpassungsschritte für ASP.NET-Projekte sind in einer JSProj-Projektdatei nicht erforderlich. Das heißt, dass Skriptdateien, die vom `data-main`-Attribut Skript-Tag verwendet werden, das auf "require.js" verweist, automatisch zur Konfiguration von "require.js" geladen werden. Die HTML-Datei, die auf "reuqire.js" verweist, wird auch als Startseite für die Anwendung verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)



