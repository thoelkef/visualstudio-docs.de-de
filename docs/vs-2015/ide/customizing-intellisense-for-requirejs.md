---
title: Anpassen von IntelliSense für RequireJS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ce0aadf455e95895309bbae4f23eb84c75935428
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201871"
---
# <a name="customizing-intellisense-for-requirejs"></a>Anpassen von IntelliSense für RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beginnend mit Visual Studio 2013 Update 4 wird Unterstützung für die beliebte RequireJS-JavaScript-Datei und das modulare Ladeprogramm unterstützt. RequireJS erleichtert das Definieren von Abhängigkeiten zwischen Codemodulen und das dynamische Laden von Modulen nur bei Bedarf. Beim Schreiben von JavaScript-Code, der RequireJS verwendet, werden IntelliSense Vorschläge für Module bereitgestellt, auf die Sie aus Ihrer Moduldefinition verwiesen oder mit Aufrufen von `require()` aus dem Code heraus verwiesen haben.  
  
 Visual Studio unterstützt standardmäßig eine sehr einfache Konfiguration zur Unterstützung von RequireJS, aber es ist üblich, dass Sie Ihre eigenen benutzerdefinierten Konfigurationseinstellungen einrichten (das heißt, Aliase für Bibliotheken definieren). Dieses Thema beschreibt die verschiedenen Möglichkeiten, über die Sie Visual Studio so anpassen können, dass es mit der einzigartigen Einrichtung Ihres Projekts funktioniert.  
  
 In diesem Thema wird Folgendes erläutert:  
  
- Anpassen von RequireJS in ASP.NET-Projekten  
  
- Anpassen von RequireJS in JSProj-Projekten, die verwendet werden, um Apache Cordova-apps, Windows Store-Apps und LightSwitch-HTML-Apps zu erstellen.  
  
## <a name="customize-requirejs-in-aspnet-projects"></a>Anpassen von RequireJS in ASP.NET-Projekten  
 Die Unterstützung für RequireJS wird automatisch aktiviert, wenn auf eine Datei mit dem Namen „require.js“ durch Ihre aktuelle JavaScript-Datei verwiesen wird. (Weitere Informationen finden Sie im Abschnitt „Bestimmen des IntelliSense-Kontexts“ unter [JavaScript IntelliSense](../ide/javascript-intellisense.md)). In ASP.NET-Projekten erfolgt das Verweisen auf „require.js“ in der Regel mithilfe einer /// \<reference/>-Anweisung in einer _references.js-Datei.  
  
### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Konfigurieren des Data-Main-Attributs in einem ASP.NET-Projekt  
 Um korrekt zu simulieren, wie Ihre App bei Ausführung funktioniert, muss der JavaScript-Editor wissen, welche Datei zuerst geladen werden soll, wenn Sie "require.js" einrichten. Dies wird in der Regel in der Anwendungs-HTML-Datei mit dem `data-main`-Attribut für das Script-Element konfiguriert, das auf "require.js" verweist, wie nachfolgend dargestellt.  
  
```html  
<script src="js/require.js" data-main="js/app.js"></script>  
```  
  
 In diesem Beispiel wird das Skript, auf das von data-main (js/app.js) verwiesen wird, unmittelbar nach "require.js" geladen. Die Datei, die sofort geladen wird, ist am besten geeignet, um zuerst die Nutzung von RequireJS zu konfigurieren (mithilfe von `require.config()`). Fügen Sie ein `data-main`-Attribut hinzu, um dem JavaScript-Editor mitzuteilen, welche Datei für `data-main` in der Anwendung verwendet werden soll, und ändern Sie dann eine /// \<reference/>-Anweisung, die in der Anwendung auf „require.js“ verweist. Sie können diese Anweisung beispielsweise für Folgendes verwenden:  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" />  
```  
  
### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Konfigurieren der Startseite der Anwendung in einem ASP.NET-Projekt  
 Wenn die app ausgeführt wird, RequireJS setzt voraus, dass relative Pfade zu Dateien (z. B. "... \\"Pfade) sind relativ zur HTML-Datei, die die Bibliothek" Require.js "geladen. Beim Schreiben von Code im Visual Studio-Editor für ein ASP.NET-Projekt, ist diese Startseite unbekannt, und Sie müssen dem Editor mitteilen, welche Startseite verwendet werden soll, wenn Sie relative Dateipfade verwenden. Fügen Sie zu diesem Zweck ein `start-page`-Attribut zu der /// \<reference/>-Anweisung hinzu.  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />  
```  
  
 Das `start-page`-Attribut gibt die URL der Seite an, wie sie in einem Browser beim Ausführen der App angezeigt würde.  
  
## <a name="customize-requirejs-in-jsproj-projects"></a>Anpassen von RequireJS in JSProj-Projekten  
 Beim Erstellen von Apps für Apache Cordova, HTML-basierte Windows Store-Apps oder LightSwitch-HTML-Apps werden JSProj-Projekte (Projektdateien mit der Erweiterung „.jsproj“) verwendet. Im Gegensatz zu ASP.NET-Projekten lesen diese Projekte Verweise auf die JS-Dateien aus HTML-Dateien, die im Projekt vorhanden sind. Aus diesem Grund wird beim Bearbeiten von JavaScript in einem Projekt JSProj Unterstützung für RequireJS aktiviert, wenn auf die JavaScript-Datei, die derzeit bearbeitet wird, in einer anderen HTML-Datei verwiesen wird, die auch auf "require.js" verweist.  
  
 Die Anpassungsschritte für ASP.NET-Projekte sind in einer JSProj-Projektdatei nicht erforderlich. Das heißt, dass Skriptdateien, die vom `data-main`-Attribut Skript-Tag verwendet werden, das auf "require.js" verweist, automatisch zur Konfiguration von "require.js" geladen werden. Die HTML-Datei, die auf "reuqire.js" verweist, wird auch als Startseite für die Anwendung verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
