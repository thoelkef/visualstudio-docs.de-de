---
title: Layout mit Dom Explorer Debuggen | Microsoft-Dokumentation
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
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a3c9b3a6ae2ed11e8512f8cf8857d27b3d0043b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850078"
---
# <a name="debug-layout-using-dom-explorer"></a>Debuggen von Layout mithilfe von DOM Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Die Registerkarte **Layout** des DOM Explorer teigt das [CSS-Verschachtelungsmodell](https://www.w3.org/TR/CSS2/box.html) für das ausgewählte Elemente in einer [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] -App, Windows Phone Store-App oder einer mit Visual Studio Tools for Apache Cordova erstellten App. Sie können die visuelle Darstellung des Verschachtelungsmodells verwenden, um die layoutbezogenen Werte, die die Darstellung der Elemente beeinflussen, zu identifizieren und zu ändern.  
  
> [!TIP]
> Änderungen, die Sie auf der Registerkarte **Layout** vornehmen, werden nicht dauerhaft übernommen. Wenn Sie permanente Änderungen am Quellcode vornehmen möchten, aktualisieren Sie die App mithilfe der Schaltfläche **Windows-App aktualisieren** (nur Windows Store- und Windows Phone Store-Apps) auf der Symbolleiste "Debuggen". Dadurch können Sie vermeiden, dass der Debugger neu gestartet wird.  
  
 Wenn Sie DOM Explorer verwenden möchten, um Aspekte des Layouts zu ändern, die im Feld Modell nicht angezeigt werden, lesen Sie [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md) und [Debuggen von CSS-Dom Explorer Stilen](../debugger/debug-css-styles-using-dom-explorer.md)  
  
## <a name="example-of-fixing-a-layout-issue"></a>Beispiel für das Beheben eines Layoutproblems  
 In diesem Beispiel wird ein Listenelement in der Hub/Pivot-Vorlage ausgewählt, dann werden die Werte des Verschachtelungsmodells interpretiert, die auf der Registerkarte **Layout** vorhanden sind, und anschließend wird einer der Eigenschaftswerte geändert, um ein Layoutproblem zu beheben.  
  
#### <a name="to-fix-the-layout-issue"></a>So beheben Sie das Layoutproblem  
  
1. Erstellen Sie in Visual Studio eine neue Store-App auf Grundlage der Projektvorlage "Hub/Pivot".  
  
2. Öffnen Sie im Ordner "shared pages\hub" hub.css.  
  
3. Ersetzen Sie den folgenden CSS-Code:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     mit diesem CSS-Code:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4. Wählen Sie entweder das Projekt "appName.WindowsPhone" oder "appName.Windows" im Projektmappen-Explorer aus, und klicken Sie dann im Kontextmenü für das Projekt auf **Als Startprojekt festlegen** .  
  
5. Wählen Sie je nach Startprojekt **Emulator 8.1 WVGA 4 inch 512MB** oder **Simulator** in der Dropdownliste auf der Symbolleiste "Debuggen" aus (der Standardwert ist**Lokaler Computer** ).  
  
     ![Debug-Ziel auswählen](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6. Drücken Sie F5, um die App im Debugmodus auszuführen.  
  
7. Öffnen Sie "Section 4" durch Blättern oder Streichen.  
  
    > [!TIP]
    > Positionieren Sie den Phone-Emulator oder den Simulator direkt neben dem Visual Studio-Fenster, sodass Ihnen die Ergebnisse der von Ihnen an den CSS-Stilen vorgenommenen Auswahl und alle Änderungen sofort angezeigt werden.  
  
     Wenn "Section 4" geladen wird, können Sie sehen, dass die unteren Bilder nicht richtig aussehen. Jedes Elementbild erscheint in der Hälfte zerteilt (wobei die linke Hälfte fehlt).  
  
8. Wechseln Sie zu Visual Studio, und klicken Sie im DOM Explorer auf **Element auswählen** (oder drücken Sie STRG+B). Dadurch wird der Auswahlmodus so geändert, dass Sie ein Element auswählen können, indem Sie darauf klicken, und die App wird in den Vordergrund geholt. Der Modus wird nach einem einzelnen Mausklick wieder gewechselt.  
  
    > [!TIP]
    > Sie können auch die Pfeilschaltflächen oder andere Methoden verwenden, um HTML-Elemente direkt im DOM Explorer auszuwählen. Weitere Informationen zum Auswählen von Elementen finden Sie unter [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. Wählen Sie im Phone-Emulator oder Simulator die graue rechte Hälfte eines der Bilder aus, das nur halb dargestellt ist. Das ausgewählte Element wird markiert, wie hier im Windows Phone-Emulator dargestellt:  
  
     ![Auswählen eines DOM-Elements](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    > Der Simulator unterstützt das Zeigen auf Elemente, um eine rechteckige Hervorhebung um DOM-Elemente anzuzeigen, bevor Sie sie auswählen. Der Windows Phone-Emulator unterstützt dies nicht.  
  
     Wenn Sie ein DOM-Element auswählen, wählt der DOM Explorer automatisch das entsprechende IMG-Element in Visual Studio aus. Das Element, das im Dom Explorer ausgewählt wird, sieht wie folgt aus:  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. Klicken Sie auf die Registerkarte **Layout** . Diese Registerkarte zeigt das Feld Modell des ausgewählten Elements an, wie hier im Windows Phone Emulator dargestellt.  
  
     ![Registerkarte "Layout" des DOM Explorer](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Diese Ansicht enthält einige nützliche Informationen zum Element:  
  
    - Die Farben entsprechen der rechteckigen Hervorhebung, die im Simulator beim Zeigen auf die Elemente angezeigt wird. Die blaue Farbe stellt die \<img> Element Abmessungen dar. Die braune Farbe stellt Randwerte dar.  
  
    - Der linke Rand (margin-left) ist festgelegt, was auf die Ursache des Problems hinweist, da er mit dem Symptom (schwarz auf der linken Seite der Bilder) übereinstimmt.  
  
    - Die Felder, die Werte von 0 Pixeln zeigen (z. B. Abstand, Rahmen und Rand) weisen darauf hin, dass die entsprechenden CSS-Eigenschaften wahrscheinlich nicht festgelegt wurden.  
  
11. Um zu sehen, wie die margin-left-Regel angewendet wird, klicken Sie auf die Registerkarte **Berechnet** , und schauen Sie unter der Regel "margin-left" nach. Sie sehen, dass die margin-left-Regel mit einem Wert von "5em" festgelegt ist, der berechnete Wert aber "66.66px" oder "146.66px" lautet, je nach Zielgerät.  
  
    > [!TIP]
    > Die Registerkarte **berechnet** zeigt, dass die margin-left-Regel im `..hubpage .hub. section4 .sub-image-row img` CSS-Selektor festgelegt ist, der in "Hub. CSS" enthalten ist. Sie müssen das Problem in dieser Demo-App beheben.  
  
     Sie können auch die Registerkarte **Layout** verwenden, um Änderungen an den Layoutwerten zu testen.  
  
12. Klicken Sie auf der Registerkarte **Layout** im Feld **Rand** auf der linken Seite des Felds auf **66.66**oder **146.66** .  
  
13. Geben Sie `0` ein und drücken Sie die EINGABETASTE. (Sie können ebenso die NACH-OBEN- und NACH-UNTEN-TASTEN verwenden, um den Wert zu ändern.)  
  
14. Wählen Sie die anderen \<img> Elemente in DOM Explorer aus, und ändern Sie Ihre margin-left-Werte in 0.  
  
15. Wechseln Sie zum Phone-Emulator bzw. zum Simulator. Die aktualisierten Werte des linken Rands wurden auf die Bilder in "Section 4" angewendet. Diese Werte werden auch auf der Registerkarte **Berechnet** unter der margin-left-Regel aktualisiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debuggen von CSS-Stilen Dom Explorer mit](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Anzeigen von DOM-Ereignislistenern](../debugger/view-dom-event-listeners.md)
