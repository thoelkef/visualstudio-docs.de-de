---
title: Dom-Ereignislistener anzeigen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693577"
---
# <a name="view-dom-event-listeners"></a>Anzeigen von DOM-Ereignislistenern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Auf der Registerkarte **Ereignisse** der Dom Explorer werden die Ereignisse angezeigt, die einem DOM-Element zugeordnet sind. Jeder oberste Knoten auf der Registerkarte **Ereignisse** stellt ein Ereignis dar, das über aktive Abonnenten verfügt. Der oberste Knoten enthält untergeordnete Knoten, die die registrierten Ereignislistener für das spezifische Ereignis darstellen. Zusätzlich zur Anzeige der Ereignislistener können Sie mithilfe dieser Registerkarte zum Speicherort des Ereignislisteners im JavaScript-Code navigieren. Die Informationen in diesem Thema gelten für Store-Apps, die mit HTML und JavaScript erstellt werden.

 Die Liste auf der Registerkarte **Ereignisse** ist dynamisch. Wenn Sie einen Ereignislistener hinzufügen, während die App ausgeführt wird, wird der neue Ereignislistener dort angezeigt. Informationen zum Hinzufügen und Entfernen von Ereignislistenern finden Sie in diesem Thema unter [Tipps zum Beheben von Problemen mit Ereignislistener](#Tips) .

> [!NOTE]
> Ereignislistener für Code Elemente, die keine DOM-Elemente sind, z `xhr` . b., werden nicht auf der Registerkarte **Ereignisse** angezeigt.

## <a name="view-event-listeners-for-dom-elements"></a>Anzeigen von Ereignislistenern für DOM-Elemente
 Dieses Beispiel zeigt eine Windows Phone-App. Die hier beschriebenen DOM Explorer-Funktionen werden auch für Windows Store-Apps unterstützt.

#### <a name="to-view-event-listeners"></a>So zeigen Sie Ereignislistener an

1. Erstellen Sie in Visual Studio eine JavaScript-App auf Grundlage der Projektvorlage "Windows Phone Pivot Application".

2. Wenn die Vorlage in Visual Studio geöffnet ist, wählen Sie **Emulator 8,1 WVGA 4in 512MB** in der Dropdown Liste auf der Symbolleiste Debuggen im Debugger aus:

     ![Debug-Ziel auswählen](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. Drücken Sie F5, um die App im Debugmodus auszuführen.

4. Wechseln Sie in der laufenden app zum **Abschnitt 3** Pivot Item.

5. Wechseln Sie zu Visual Studio (ALT+TAB oder F12).

6. Klicken Sie im DOM Explorer in der rechten oberen Ecke auf `Find`.

7. Geben Sie `ListView`ein, und drücken Sie die EINGABETASTE.

8. Wählen Sie ggf. die Schaltfläche **weiter** aus, um das Element zu suchen `DIV` , das das Steuerelement darstellt `ListView` (dieses Element hat den `data-win-control` Wert `WinJS.UI.ListView` ).

     Das `DIV`-Element sollte nun im DOM Explorer ausgewählt werden.

9. Wählen Sie die Registerkarte **Ereignisse** im Bereich auf der rechten Seite DOM Explorer aus.

     Ihnen werden die Ereignisse angezeigt, die aktive Abonnenten für das `DIV`-Element haben, wie an dieser Stelle dargestellt.

     ![Registerkarte "Ereignisse" des DOM Explorer](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Um die Ereignislistener für diese Ereignisse zu suchen, klicken Sie auf die zugeordneten JavaScript-Dateilinks.

11. Um die Ereignislistener für übergeordnete Elemente in der DOM-Hierarchie schnell zu identifizieren, wählen Sie ein übergeordnetes Element in der Hierarchieliste unten im DOM Explorer aus.

     ![Übergeordnete Element in der DOM-Hierarchie auswählen](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     Auf der Registerkarte **Ereignisse** werden Ereignislistener für alle Elemente angezeigt, die Sie in der Liste Hierarchie auswählen.

### <a name="tips-for-resolving-issues-with-event-listeners"></a><a name="Tips"></a> Tipps zum Beheben von Problemen mit Ereignislistenern
 In einigen App-Szenarien müssen Ereignislistener explizit mithilfe von [RemoveEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx)entfernt werden. Verwenden Sie die Registerkarte **Ereignisse** im Dom Explorer, um zu testen, ob Ereignislistener beim Ausführen von Code aus DOM-Elementen entfernt wurden. Hier sind einige Tipps, wie diese Probleme gelöst werden können:

- Für apps, die das in den Visual Studio- [Projektvorlagen](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx)implementierte einseitige Navigations Modell verwenden, ist es in der Regel nicht erforderlich, Ereignislistener zu entfernen, die für Objekte registriert sind, wie z. b. DOM-Elemente, die Teil einer Seite sind. In diesem Szenario haben das DOM-Element und die zugehörigen Ereignislistener dieselbe Lebensdauer und können per Garbage Collection bereinigt werden.

- Falls die Lebensdauer des DOM-Elements oder des Objekts kürzer oder länger ist als die des zugehörigen Ereignislisteners, müssen Sie ggf. die Methode `removeEventListener` aufrufen. Wenn Sie beispielsweise das Ereignis `window.onresize` verwenden, müssen Sie den Ereignislistener entfernen, sobald Sie zur Ereignisbehandlung weg von der Seite navigieren.

- Wenn `removeEventListener` den angegebenen Listener nicht entfernen kann, kann dieser in einer anderen Instanz des Objekts aufgerufen werden. Sie können das Problem mithilfe der Methode [Bind Method (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) beheben, wenn Sie den Listener hinzufügen.

- Um einen Ereignislistener zu entfernen, der mit der [Bind-Methode (Funktion)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) oder mit einer anonymen Funktion hinzugefügt wurde, speichern Sie eine Instanz der Funktion, wenn Sie den Listener hinzufügen. Dies ist eine sichere Methode zur Verwendung dieser Vorgehensweise:

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

- Sie können einen Ereignislistener nicht mithilfe von `removeEventListener` entfernen, wenn Sie ihn mit dem `obj.on<eventname>`-Attribut hinzugefügt haben, z. B. `window.onresize = handlerFunc`.

- Verwenden Sie den JavaScript-arbeitsspeicheranalyzer für [JavaScript-Speicher](../profiling/javascript-memory.md) in Ihrer APP. Ereignislistener, die explizit entfernt werden müssen, erscheinen möglicherweise als Speicherverlust.

## <a name="see-also"></a>Weitere Informationen

- [Schnellstart: Debug HTML and CSS (Schnellstart: Debuggen von HTML und CSS)](../debugger/quickstart-debug-html-and-css.md)
- [Debuggen von CSS-Stilen mithilfe von DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md)
- [Debuggen von Layout mithilfe von DOM Explorer](../debugger/debug-layout-using-dom-explorer.md)