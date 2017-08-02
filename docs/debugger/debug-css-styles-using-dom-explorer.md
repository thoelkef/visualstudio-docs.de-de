---
title: "Debuggen von CSS-Stilen mithilfe von DOM Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "CSS-Stile [Windows Store-Apps], Debuggen"
  - "CSS-Regeln [Windows Store-Apps], Debuggen"
  - "CSS-Debuggen [Windows Store-Apps]"
  - "Debuggen, CSS-Regeln [Windows Store-Apps]"
  - "HTML-Debuggen [Windows Store-Apps]"
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 44
---
# Debuggen von CSS-Stilen mithilfe von DOM Explorer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Gilt für Windows und Windows Phone](~/docs/debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Wenn Sie Windows Store\- und Windows Phone Store\-Apps sowie mit Visual Studio\-Tools für Apache Cordova erstellte Apps debuggen, können Sie CSS\-Regeln für ausgewählte DOM\-Elemente und ihre untergeordneten Elemente anzeigen und ändern.  
  
 Im DOM Explorer werden auf den Registerkarten **Formatvorlagen** und **Berechnet** die CSS\-Regeln aufgeführt, die für ein ausgewähltes Element gelten. Die Regeln werden in der Reihenfolge ihrer Spezifität entsprechend den CSS\-Vorrangigkeitsregeln angezeigt. Die Regeln oben in einer Auswahl oder Formatvorlage auf einer Registerkarte \(die spezifischsten Regeln\) sind die letzten, die auf das ausgewählte Element angewendet werden, und die Regeln unten in einer Auswahl oder Formatvorlage sind die ersten, die angewendet werden. Wenn Regeln angewendet werden, überschreiben sie zuvor angewendete Regeln.  
  
 Die Registerkarten **Formatvorlagen**, **Berechnet** und **Änderungen** enthalten unterschiedliche Ansichten von Formatinformationen.  
  
-   Verwenden Sie die Registerkarte **Formatvorlagen**, um die Regeln anzuzeigen, die nach CSS\-Auswahlnamen angeordnet sind, wie z. B. `html, body`. Auf dieser Registerkarte können Sie auch bestimme Formatvorlagen aktivieren oder deaktivieren, Werte manuell bearbeiten und die unmittelbaren Ergebnisse dieser Änderungen anzeigen.  
  
-   Verwenden Sie die Registerkarte **Berechnet**, um die berechneten Werte einer Formatvorlage anzuzeigen. Wenn Sie beispielsweise eine Größe auf "1em" festgelegt haben, ist der von Internet Explorer berechnete Wert möglicherweise "16px". Formatvorlagen auf dieser Registerkarte sind nach Formatvorlagenname wie z. B. `height` angeordnet. Auf dieser Registerkarte können Sie auch bestimme Formatvorlagen aktivieren oder deaktivieren, Werte manuell bearbeiten und die unmittelbaren Ergebnisse dieser Änderungen anzeigen.  
  
    > [!NOTE]
    >  In Visual Studio 2013 Update 2 wurden die in der Registerkarte **Ablaufverfolgung** bereitgestellten Informationen mit der Registerkarte **Berechnet** zusammengeführt und **Ablaufverfolgung** entfernt.  
  
-   Verwenden Sie die Registerkarte **Änderungen** \(nur Windows Store\- und Windows Phone Store\-Apps\), um CSS\-Formatvorlagen zu identifizieren und nachzuverfolgen, die Sie während einer Debugsitzung geändert haben.  
  
> [!TIP]
>  Änderungen, die Sie an Formatvorlagen auf den Registerkarten **Formatvorlagen** und **Berechnet** vornehmen, sind nicht dauerhaft. Sie gehen nach dem Beenden des Debuggens verloren. Um Quellcode zu ändern und Seiten neu zu laden, ohne den Debugger zu beenden und neu zu starten, aktualisieren Sie die App mithilfe der \-Schaltfläche ![Schaltfläche "Windows&#45;App aktualisieren"](~/docs/debugger/media/js_refresh.png "JS\_Refresh") \(**Windows\-App aktualisieren**\) auf der Symbolleiste **Debuggen** \(nur Windows Store\- und Windows Phone Store\-Apps\). Weitere Informationen finden Sie unter [Aktualisieren einer App \(JavaScript\)](../debugger/refresh-an-app-javascript.md).  
  
## Beispiel für das Beheben einer CSS\-Regel  
 Dieses Beispiel zeigt, wie Sie CSS\-Regeln überprüfen und ein Problem mit einer Formatvorlage debuggen. Nehmen wir in diesem Beispiel an, dass Sie die Farbe einer Schriftart ändern möchten, die für die Anzeige von Gruppentiteln in der Vorlage [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]"Split App" verwendet wird.  
  
> [!NOTE]
>  Dieses Beispiel zeigt eine Windows Store\-App, doch gelten alle gezeigten DOM Explorer\-Funktionen auch für eine Windows Phone Store\-App und – mit Ausnahme der Registerkarte "Änderungen" – auch für eine App, die mit Visual Studio\-Tools für Apache Cordova erstellt wurde.  
  
#### So zeigen Sie CSS\-Regeln an und ändern diese  
  
1.  Erstellen Sie in Visual Studio eine [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]\-App mit JavaScript und HTML in der Projektvorlage "Split App".  
  
2.  Öffnen Sie im **Projektmappen\-Explorer** items.css. \(Sie finden items.css im Seitenordner.\)  
  
3.  Ersetzen Sie den folgenden CSS\-Code:  
  
    ```css  
    .itemspage .itemslist .item { -ms-grid-columns: 1fr; -ms-grid-rows: 1fr 90px; display: -ms-grid; height: 250px; width: 250px; }  
    ```  
  
     durch diesen:  
  
    ```css  
    .itemspage .itemslist .item { -ms-grid-columns: 1fr; -ms-grid-rows: 1fr 90px; display: -ms-grid; height: 250px; width: 250px; color: #ff6a00; }  
    ```  
  
     Hierdurch wird eine Formatvorlage hinzugefügt, die die Farbe \#ff6a00 \(orange\) für jedes Element in der Liste angibt. Die CSS\-Auswahl, `.itemspage .itemslist .item`, gibt einen Satz von Klassennamen für DIV\-Elemente in items.html an, die als geschachtelte Elemente im aktiven DOM angezeigt werden. Das DIV\-Element `item` gibt die Listenelemente an.  
  
4.  Wählen Sie in der Dropdownliste auf der Symbolleiste **Debuggen** die Option **Simulator** aus \(**Lokaler Computer** ist der Standardwert\).  
  
     ![Debug&#45;Zielliste auswählen](../debugger/media/js_select_target.png "JS\_Select\_Target")  
  
5.  Drücken Sie F5, um die App im Debugmodus auszuführen.  
  
     Wenn die Anwendung vollständig geladen ist, schauen Sie sich die Überschriften der Listenelemente wie z. B. **Gruppentitel: 1** an. Da die Farbe unverändert ist, wurde Orange folglich nicht auf die Titel angewendet. Die Ursache des Fehlers wird ermittelt und im DOM Explorer mithilfe der CSS\-Registerkarten behoben.  
  
    > [!TIP]
    >  Nachdem die App im Simulator angezeigt wird, positionieren Sie den Simulator rechts neben dem Visual Studio\-Fenster, sodass Sie die Ergebnisse der Auswahl und Änderungen, die Sie an den CSS\-Formatvorlagen vornehmen, sofort sehen können.  
  
6.  Wechseln Sie zu Visual Studio, und klicken Sie im DOM Explorer auf **Element auswählen** \(oder drücken Sie STRG\+B\). Dadurch wird der Auswahlmodus so geändert, dass Sie ein Element auswählen können, indem Sie darauf klicken, und die App wird in den Vordergrund geholt. Der Modus wird nach einem einzelnen Mausklick wieder gewechselt. Das Beispiel zeigt die Schaltfläche **Element auswählen**.![Schaltfläche "Element auswählen" im DOM Explorer](../debugger/media/js_dom_select_element_button.png "JS\_DOM\_Select\_Element\_Button")  
  
    > [!TIP]
    >  Sie können HTML\-Elemente auch direkt in DOM Explorer auswählen. Weitere Informationen zum Auswählen von Elementen finden Sie unter [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7.  Bewegen Sie im linken Bereich der Startseite den Mauszeiger im Simulator über den Titel des ersten Elements in der Liste **Gruppentitel: 1**. Der Titel wird wie hier gezeigt hervorgehoben:  
  
     ![Verwendung der Schaltfläche "Element auswählen"](../debugger/media/js_css_select_element.png "JS\_CSS\_Select\_Element")  
  
    > [!NOTE]
    >  Der Windows Phone\-Emulator unterstützt das Hervorheben von Elementen durch Zeigen mit dem Mauszeiger nur teilweise.  
  
8.  Klicken Sie auf den umrandeten Titel. DOM Explorer wählt automatisch das entsprechende HTML\-Element aus, das diesem ähnelt.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Wenn Sie das H4\-Element in DOM Explorer auswählen, zeigen die DOM Explorer\-Registerkarten nun die Regeln an, die dem H4\-Element verknüpft sind. In diesem Beispiel ist die Registerkarte **Berechnet** mit der geöffneten `color`\-Eigenschaft zu sehen:  
  
     ![Registerkarte "Formatvorlagen verfolgen" im DOM Explorer](../debugger/media/js_css_styles.png "JS\_CSS\_Styles")  
  
     Diese Ansicht bietet nützliche Informationen zu den Regeln, die der `color`\-Formatvorlage zugeordnet sind, wie im folgenden Beispiel dargestellt.  
  
    -   Die CSS\-Auswahl, die Sie in items.css geändert haben, `.itemspage .itemslist .item`, wird in der endgültigen Formatvorlagenberechnung nicht verwendet \(sie wird in durchgestrichenem Text dargestellt\). Einige weitere Vorkommen der Formatvorlage `color` werden ebenfalls nicht verwendet.  
  
        > [!TIP]
        >  Bei längeren Auswahlnamen wird der vollständige Name in einer QuickInfo angezeigt.  
  
    -   Der endgültige berechnete CSS\-Wert, `rgba(255, 255, 255, 0.87)`, wird speziell für die folgende CSS\-Auswahl festgelegt: `.itemspage .itemslist .item .item-overlay .item-title`. Diese wird auch in items.css definiert.  
  
        > [!TIP]
        >  Nachdem Sie nun wissen, wo die Titelfarbe festgelegt wird, wissen Sie auch, wo Sie sie ändern können. Sie können Änderungen in DOM Explorer allerdings auch testen, ohne die Anwendung zu aktualisieren, wie in den verbleibenden Schritten gezeigt.  
  
9. Deaktivieren Sie das Kontrollkästchen für das erste Vorkommen der Formatvorlage `color`, die für die Auswahl `.itemspage .itemslist .item .item-overlay .item-title` gilt. Jetzt sehen Sie im Simulator, dass die Farbe der Elementnamen sich in orange ändert, so wie wir es beabsichtigt haben, und dass die Auswahl, die wir in CSS geändert haben, `.itemspage .itemslist .item`, nicht mehr überschrieben wird \(das heißt, sie wird nicht mehr in durchgestrichenem Text dargestellt\). In diesem Beispiel sehen Sie die Registerkarte **Berechnet**, nachdem die Kontrollkästchen deaktiviert wurden.  
  
     ![Die Registerkarte "Berechnet" nach der Aktualisierung der CSS&#45;Formatvorlage](../debugger/media/js_css_styles_fixed.png "JS\_CSS\_Styles\_Fixed")  
  
10. Wählen Sie die Registerkarte **Änderungen** aus.  
  
     Verwenden Sie die Registerkarte **Änderungen**, um Änderungen an Formatvorlagen zu identifizieren und nachzuverfolgen, die Sie während einer Debugsitzung vorgenommen haben. Die folgende Abbildung zeigt die jetzt überschriebene `.itemspage .itemslist .item .item-overlay .item-title`\-Auswahl in der Registerkarte **Änderungen**.  
  
     ![Registerkarte "Änderungen" des DOM Explorer](../debugger/media/js_css_styles_changes.png "JS\_CSS\_Styles\_Changes")  
  
11. Sie können die Werte der CSS\-Formatvorlage auch manuell bearbeiten und das unmittelbare Ergebnis auf der Registerkarte **Formatvorlagen** anzeigen.  
  
12. Wählen Sie die Registerkarte **Formatvorlagen** aus.  
  
13. Öffnen Sie die Formatvorlagenauswahl `.itemspage .itemslist .item .item-overlay .item-title`.  
  
14. Wählen Sie das erste Vorkommen der Formatvorlage `color` aus, und doppelklicken Sie auf den Eigenschaftswert `rgb(255, 255, 255, 0.87)`.  
  
15. Ändern Sie diesen Wert über die Tastatur. Ändern Sie ihn in `rgb(255, 255, 0, 0.87)`, und drücken Sie die EINGABETASTE. Im Simulator ändert sich die Farbe der Elementnamen in gelb.  
  
16. Um Änderungen an der CSS\-Quelldatei vorzunehmen, klicken Sie auf der Registerkarte **Formatvorlagen** auf den Link **items.css**. Dadurch wird "items.css" geöffnet. Hier können Sie den Wert der Formatvorlage `color` in Ihrem App\-Code ändern. Um die App zu aktualisieren, ohne den Debugger zu beenden und neu zu starten, klicken Sie auf der Symbolleiste **Debuggen** auf die Schaltfläche ![Schaltfläche "Windows&#45;App aktualisieren"](~/docs/debugger/media/js_refresh.png "JS\_Refresh") \(**Windows\-App aktualisieren**\).  
  
## Siehe auch  
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debuggen von Layout mithilfe von DOM Explorer](../debugger/debug-layout-using-dom-explorer.md)   
 [Anzeigen von DOM\-Ereignislistenern](../debugger/view-dom-event-listeners.md)   
 [Produktsupport und Barrierefreiheit](http://go.microsoft.com/fwlink/?LinkId=253502)