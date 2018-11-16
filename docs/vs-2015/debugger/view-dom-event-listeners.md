---
title: Anzeigen von DOM-Ereignislistenern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1e0cf0abc35c87de3c7caa3ed00e57cb07cf987
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727377"
---
# <a name="view-dom-event-listeners"></a>Anzeigen von DOM-Ereignislistenern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt Sie für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "Windows_and_phone_content")  
  
 Die **Ereignisse** DOM Explorer auf der Registerkarte zeigt die Ereignisse, die ein DOM-Element zugeordnet sind. Jeder oberste Knoten in der **Ereignisse** Registerkarte stellt ein Ereignis, das aktive Abonnenten verfügt. Der oberste Knoten enthält untergeordnete Knoten, die die registrierten Ereignislistener für das spezifische Ereignis darstellen. Zusätzlich zur Anzeige der Ereignislistener können Sie mithilfe dieser Registerkarte zum Speicherort des Ereignislisteners im JavaScript-Code navigieren. Die Informationen in diesem Thema gelten für Store-Apps, die mit HTML und JavaScript erstellt werden.  
  
 Die Liste der **Ereignisse** Registerkarte ist dynamisch. Wenn Sie einen Ereignislistener hinzufügen, während die App ausgeführt wird, wird der neue Ereignislistener dort angezeigt. Informationen zum Hinzufügen und Entfernen von Ereignislistenern finden Sie unter [Tipps zur Problembehebung bei Ereignislistenern](#Tips) in diesem Thema.  
  
> [!NOTE]
>  Ereignislistener für Codeelemente, die DOM-Elemente, wie z. B. nicht `xhr`, nicht angezeigt, auf die **Ereignisse** Registerkarte.  
  
## <a name="view-event-listeners-for-dom-elements"></a>Anzeigen von Ereignislistenern für DOM-Elemente  
 Dieses Beispiel zeigt eine Windows Phone-App. Die hier beschriebenen DOM Explorer-Funktionen werden auch für Windows Store-Apps unterstützt.  
  
#### <a name="to-view-event-listeners"></a>So zeigen Sie Ereignislistener an  
  
1.  Erstellen Sie in Visual Studio eine JavaScript-App auf Grundlage der Projektvorlage "Windows Phone Pivot Application".  
  
2.  Wählen Sie die Vorlage in Visual Studio geöffnet, **Emulator 8.1 WVGA 4 Zoll 512MB** in der Dropdown-Liste auf der Symbolleiste "Debuggen" im Debugger:  
  
     ![Debugziel auswählen](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
3.  Drücken Sie F5, um die App im Debugmodus auszuführen.  
  
4.  Wechseln Sie in der ausgeführten app zu den **Abschnitt 3** Pivot-Element.  
  
5.  Wechseln Sie zu Visual Studio (ALT+TAB oder F12).  
  
6.  Klicken Sie im DOM Explorer in der rechten oberen Ecke auf `Find`.  
  
7.  Typ `ListView`, und drücken Sie dann die EINGABETASTE.  
  
8.  Wählen Sie bei Bedarf die **Weiter** Schaltfläche finden die `DIV` Element, dargestellt die `ListView` Steuerelement (dieses Element verfügt über eine `data-win-control` Wert `WinJS.UI.ListView`).  
  
     Das `DIV`-Element sollte nun im DOM Explorer ausgewählt werden.  
  
9. Wählen Sie die **Ereignisse** Registerkarte im Bereich auf der rechten Seite des DOM Explorers.  
  
     Ihnen werden die Ereignisse angezeigt, die aktive Abonnenten für das `DIV`-Element haben, wie an dieser Stelle dargestellt.  
  
     ![Registerkarte "Ereignisse" im DOM Explorer](../debugger/media/js-dom-events.png "JS_DOM_Events")  
  
10. Um die Ereignislistener für diese Ereignisse zu suchen, klicken Sie auf die zugeordneten JavaScript-Dateilinks.  
  
11. Um die Ereignislistener für übergeordnete Elemente in der DOM-Hierarchie schnell zu identifizieren, wählen Sie ein übergeordnetes Element in der Hierarchieliste unten im DOM Explorer aus.  
  
     ![Auswählen von übergeordneten Elementen in der DOM-Hierarchie](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")  
  
     Die **Ereignisse** Registerkarte zeigt die Ereignislistener für jedes Element, das Sie in der Hierarchieliste auswählen.  
  
###  <a name="Tips"></a> Tipps zur Problembehebung bei Ereignislistenern  
 In einigen app-Szenarien müssen Ereignislistener müssen entfernt werden, explizit mit [RemoveEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Verwenden der **Ereignisse** Registerkarte im DOM Explorer zum Überprüfen, ob Ereignislistener beim Ausführen von Code aus dem DOM-Elemente entfernt wurden. Hier sind einige Tipps, wie diese Probleme gelöst werden können:  
  
-   Für apps, mit denen des navigationsmodells für Einzelseiten-implementiert, in der Visual Studio [Projektvorlagen](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx), es ist nicht in der Regel erforderlich, um für Objekte wie DOM-Elemente, die Teil einer Seite sind, registrierte Ereignislistener zu entfernen. In diesem Szenario haben das DOM-Element und die zugehörigen Ereignislistener dieselbe Lebensdauer und können per Garbage Collection bereinigt werden.  
  
-   Falls die Lebensdauer des DOM-Elements oder des Objekts kürzer oder länger ist als die des zugehörigen Ereignislisteners, müssen Sie ggf. die Methode `removeEventListener` aufrufen. Wenn Sie beispielsweise das Ereignis `window.onresize` verwenden, müssen Sie den Ereignislistener entfernen, sobald Sie zur Ereignisbehandlung weg von der Seite navigieren.  
  
-   Wenn `removeEventListener` den angegebenen Listener nicht entfernen kann, kann dieser in einer anderen Instanz des Objekts aufgerufen werden. Sie können die [bind-Methode (Funktion)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md) Methode, um dieses Problem zu beheben, wenn Sie den Listener hinzufügen.  
  
-   Um einen Ereignislistener zu entfernen, die hinzugefügt wurde, indem Sie entweder [bind-Methode (Funktion)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md) oder speichern Sie eine Instanz der Funktion mit einer anonymen Funktion, wenn Sie den Listener hinzufügen. Dies ist eine sichere Methode zur Verwendung dieser Vorgehensweise:  
  
    ```javascript  
    // You could use the following code within the constructor function of an object, or  
    // in the ready function of a PageControl object (Store app).  
    this.storedHandler = this._handlerFunc.bind(this);  
    elem.addEventListener('mouseup', this.storedHandler);  
  
    // In this example, add the following code in the PageControl object's unload function.  
    elem.removeEventListener('mouseup', this.storedHandler);  
  
    ```  
  
     Wenn Sie den folgenden Code verwenden, statt einen Verweis auf die gebundene Funktion zu speichern, können Sie den Ereignislistener nicht explizit entfernen:  
  
    ```javascript  
    // Avoid this pattern. No reference to the bound function is available.  
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));  
    ```  
  
-   Sie können einen Ereignislistener nicht mithilfe von `removeEventListener` entfernen, wenn Sie ihn mit dem `obj.on<eventname>`-Attribut hinzugefügt haben, z. B. `window.onresize = handlerFunc`.  
  
-   Verwenden Sie die JavaScript-Speicheranalyse zum [JavaScript-Memory](../profiling/javascript-memory.md) in Ihrer app. Ereignislistener, die explizit entfernt werden müssen, erscheinen möglicherweise als Speicherverlust.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debuggen von CSS-Stilen mithilfe von DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Debuggen von Layout mithilfe von DOM Explorer](../debugger/debug-layout-using-dom-explorer.md)



