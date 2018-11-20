---
title: Bearbeiten von Tests der programmierten UI mithilfe des Editors für Tests der programmierten UI | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1bf24c24a60a37fd8fc5859d216c34eaa2e9b4f8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951256"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Bearbeiten von Tests der programmierten UI mithilfe des Editors für Tests der programmierten UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Editor für Tests der programmierten UI können Sie Tests der programmierten UI mühelos ändern. Er ermöglicht das Suchen, Anzeigen und Bearbeiten von Eigenschaften der Testmethoden und UI-Aktionen. Darüber hinaus können Sie mit der UI-Steuerelementzuordnung die entsprechenden Steuerelemente anzeigen und bearbeiten.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Warum sollte ich das tun?  
 Mit dem Editor für Tests der programmierten UI sind Sie schneller und effizienter, als wenn Sie den Code in den Testmethoden der programmierten UI mithilfe des Code-Editors bearbeiten. Mit dem Editor für Tests der programmierten UI können Sie mithilfe der Symbolleiste und der Kontextmenüs schneller die den UI-Aktionen und -Steuerelementen zugeordneten Eigenschaftswerte finden und bearbeiten. Mit der Symbolleiste des Editors für Tests der programmierten UI können Sie beispielsweise die folgenden Befehle ausführen:  
  
 ![UI-Test-Editor](../test/media/uitesteditor.png "UITestEditor")  
  
1.  Mit [Suchen](../ide/finding-and-replacing-text.md) können Sie nach UI-Aktionen und -Steuerelementen suchen.  
  
2.  Mit[Löschen](#CodedUITestEditor_DeleteUIActions) können Sie unerwünschte UI-Aktionen entfernen.  
  
3.  Mit**Umbenennen** können Sie die Namen für Testmethoden und Steuerelemente ändern.  
  
4.  **Eigenschaften** Öffnet das Fenster Eigenschaften für das ausgewählte Element.  
  
5.  Mit[In eine neue Methode aufteilen](#CodedUITestEditor_SplitMethods) können Sie UI-Aktionen modularisieren.  
  
6.  Mit[Code verschieben](#CodedUITestEditor_MoveMethods) können Sie benutzerdefinierten Code zu Testmethoden  hinzufügen.  
  
7.  Mit[Verzögerung einfügen vor](#CodedUITestEditor_InsertDelay) können Sie eine Pause in Millisekunden vor einer UI-Aktion hinzufügen.  
  
8.  Mit[UI-Steuerelement suchen](#CodedUITestEditor_LocateUIControl) wird die Position des Steuerelements in der Benutzeroberfläche der getesteten Anwendung ermittelt.  
  
9. Mit[Alle suchen](#CodedUITestEditor_LocateDecendants) können Sie Steuerelementeigenschaften und bedeutende Änderungen an den Steuerelementen der Anwendung überprüfen.  
  
## <a name="how-do-i-do-this"></a>Vorgehensweise  
 Beim Öffnen der Datei „UIMap.uitest“ in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], die mit dem Test der programmierten UI im Testprojekt der programmierten UI verbunden ist, wird der Test der programmierten UI automatisch im Editor für Tests der programmierten UI angezeigt. In den folgenden Verfahren wird beschrieben, wie Sie mithilfe der Symbolleiste und den Kontextmenüs des Editors die Testmethoden, Eigenschaften für die UI-Aktionen und Steuerelemente finden und bearbeiten können.  
  
## <a name="open-a-coded-ui-test"></a>Einen Test der codierten UI öffnen  
 Mit dem Editor für Tests der programmierten UI können Sie den Visual C#- und Visual Basic-basierten Test der programmierten UI anzeigen und bearbeiten.  
  
 ![Kontextmenü mit Test-Generator der programmierten UI](../test/media/editcodeduitest.png "EditCodedUITest")  
  
 Öffnen Sie im Projektmappen-Explorer das Kontextmenü **UIMap.uitest** , und wählen Sie **Öffnen**aus. Der Test der codierten UI wird im Editor für den Test der codierten UI angezeigt. Sie können nun aufgezeichnete Methoden, Aktionen und entsprechende Steuerelemente im Test der programmierten UI anzeigen und bearbeiten.  
  
> [!TIP]
>  Beim Auswählen einer UI-Aktion, die in einer Methode im Bereich **UI-Aktionen** enthalten ist, wird das entsprechende Steuerelement hervorgehoben. Sie können auch die UI-Aktion oder die Steuerelementeigenschaften ändern.  
  
 Der Editor für Tests der programmierten UI*wird nicht angezeigt* .  
 Möglicherweise verwenden Sie eine Version von Visual Studio Enterprise, die älter als 2012 ist. Der Editor für Tests der programmierten UI stand auch in Visual Studio 2010 Feature Pack 2 mit einem MSDN-Abonnement zur Verfügung. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Microsoft Visual Studio 2010 Feature Pack 2](http://go.microsoft.com/fwlink/?LinkID=204119).  
  
##  <a name="CodedUITestEditor_EditActionAndControlProperties"></a> Eigenschaften der UI-Aktionen und ihre entsprechenden Steuerelementeigenschaften ändern  
 Mit dem Editor für Tests der programmierten UI, können Sie leicht alle UI-Aktionen in den Testmethoden finden und anzeigen. Wenn Sie die UI-Aktion im Editor auswählen, wird das entsprechende Steuerelement automatisch hervorgehoben. Wenn Sie ein Steuerelement auswählen, werden entsprechend die zugeordneten UI-Aktionen hervorgehoben. Wenn Sie eine UI-Aktion oder ein -Steuerelement auswählen, können Sie dann einfach das Fenster „Eigenschaften“ verwenden, um die entsprechenden Eigenschaften zu  ändern.  
  
 ![Eigenschaften der UI-Aktion](../test/media/codeduiedituiaction.png "CodedUIEditUIAction")  
Bearbeiten der Eigenschaften der UI-Aktion  
  
 Erweitern Sie zum Ändern der Eigenschaften einer UI-Aktion die Testmethode im Bereich **UI-Aktion** , die die UI-Aktion mit den zu bearbeitenden Eigenschaften enthält. Wählen Sie die UI-Aktion aus, und ändern Sie dann die Eigenschaften im Fenster „Eigenschaften“.  
  
 Wenn ein Server beispielsweise nicht verfügbar ist und in Ihrem Webbrowser die UI-Aktion **Zur Webseite <http://Contoso1/default.aspx’> wechseln** vorhanden ist, können Sie die URL in `‘http://Contoso2/default.aspx’` ändern.  
  
 ![Steuerelementeigenschaften](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp")  
Bearbeiten von Steuerelementeigenschaften  
  
 Die Änderung der Eigenschaften eines Steuerelements erfolgt auf die gleiche Weise wie die der UI-Aktionen. Wählen Sie im Bereich **UI-Steuerelementzuordnung** das zu bearbeitende Steuerelement aus, und bearbeiten Sie seine Eigenschaften im Fenster „Eigenschaften“.  
  
 Ein Entwickler könnte z. B. die **(ID)** -Eigenschaft auf einem Schaltflächen-Steuerelement im Quellcode für die getestete Anwendung von „idSubmit“ in „idLogin“ geändert haben. Wenn die **(ID)** -Eigenschaft in der Anwendung geändert wurde, kann der Test der programmierten UI nicht das Schaltflächen-Steuerelement finden, und es wird ein Fehler ausgegeben. In diesem Fall kann der Tester die Auflistung **Sucheigenschaften** öffnen und die **ID** -Eigenschaft auf den neuen Wert festlegen, den der Entwickler in der Anwendung verwendet hat. Der Tester kann auch den Eigenschaftswert von **Anzeigename** von „Submit“ in „Login“ ändern. Durch diese Änderung wird die zugeordnete UI-Aktion im Editor für Tests der programmierten UI von „Schaltfläche 'Submit' auswählen“ in „Schaltfläche 'Login' auswählen" geändert.  
  
 Nachdem Sie die Änderungen abgeschlossen haben, speichern Sie die Änderungen in der Datei „UIMap.Designer“, indem Sie auf der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Symbolleiste **Speichern** auswählen.  
  
 *Was sollte ich noch wissen?*  
 **Tipps**  
  
-   ![Tipp](../test/media/tip.png "Tip") Wenn das Fenster „Eigenschaften“ nicht angezeigt wird, halten Sie **ALT** gedrückt, und drücken Sie **EINGABE**, oder drücken Sie alternativ **F4**.  
  
-   ![Tipp](../test/media/tip.png "Tip") Wählen Sie **Rückgängig** aus dem Menü **Bearbeiten** aus, oder drücken Sie STRG+Z, wenn Sie die an den Eigenschaften vorgenommenen Änderungen rückgängig machen möchten.  
  
-   ![Tipp](../test/media/tip.png "Tip") Mit der Schaltfläche **Suchen** in der Symbolleiste des Editors für Tests der programmierten UI können Sie das Tool zum Suchen und Ersetzen in Visual Studio öffnen. Anschließend können Sie mit dem Steuerelement „Suchen“ nach einer UI-Aktion im Editor für Tests der programmierten UI suchen. Sie können z. B. die Option „Auf die Schaltfläche 'Anmelden' klicken“ suchen. Dies kann bei umfangreichen Tests hilfreich sein. Beachten Sie, dass Sie die Ersetzungsfunktion nicht im Tool zum Suchen und Ersetzen im Editor für Tests der programmierten UI verwenden können. Weitere Informationen finden Sie unter „Steuerelement Suchen‘“ in [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md).  
  
-   ![Tipp](../test/media/tip.png "Tip") Manchmal kann die Darstellung der Position der Steuerelemente in der Benutzeroberfläche der getesteten Anwendung schwierig sein. Zu den Funktionen des Editors für Tests der programmierten UI zählen die Möglichkeiten zum Auswählen eines Steuerelements, das in der UI-Steuerelementzuordnung aufgeführt ist, und zum Anzeigen der Position in der getesteten Anwendung. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Suchen eines UI-Steuerelements in der getesteten Anwendung](#CodedUITestEditor_LocateUIControl) im weiteren Verlauf dieses Themas.  
  
-   ![Tipp](../test/media/tip.png "Tip") Möglicherweise müssen Sie das Containersteuerelement erweitern, das das zu bearbeitende Steuerelement enthält. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Suchen eines Steuerelements und seiner Nachfolgerelemente](#CodedUITestEditor_LocateDecendants) im weiteren Verlauf dieses Themas.  
  
##  <a name="CodedUITestEditor_DeleteUIActions"></a> Unerwünschte UI-Aktionen löschen  
 Sie können unerwünschte UI-Aktionen in dem Test der programmierten UI leicht entfernen.  
  
 ![UI-Aktion löschen](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")  
  
 Erweitern Sie im Bereich **UI-Aktion** die Testmethode, die die zu löschende UI-Aktion enthält. Öffnen Sie das Kontextmenü für die UI-Aktion, und wählen Sie dann **Löschen**.  
  
##  <a name="CodedUITestEditor_SplitMethods"></a> Eine Testmethode in zwei separate Methoden aufteilen  
 Sie können eine Testmethode aufteilen, um die UI-Aktionen zu optimieren und zu modularisieren. Beispielsweise kann der Test eine einzelne Testmethode mit UI-Aktionen in zwei Containersteuerelementen beinhalten. Die UI-Aktionen werden ggf. besser in zwei Methoden modularisiert, die einem Container entsprechen.  
  
 ![Teilen einer Testmethode](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")  
  
 ![Zwei Testmethoden](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")  
  
 Erweitern Sie im Bereich **UI-Aktion** die Testmethode, die Sie in zwei separate Methoden aufteilen möchten, und wählen Sie die UI-Aktion, die als Anfang der neuen Testmethode dienen soll. Öffnen Sie entweder das Kontextmenü für die UI-Aktion, und wählen Sie dann **In eine neue Methode aufteilen**, oder wählen Sie die Schaltfläche **In eine neue Methode aufteilen** auf der Symbolleiste des Editors für Tests der programmierten UI. Die neue Testmethode wird im Bereich „UI-Aktionen“ angezeigt. Sie enthält UI-Aktionen, beginnend mit der Aktion, in der Sie die Aufteilung angegeben haben.  
  
 Wenn Sie die Aufteilung der Methode abgeschlossen haben, speichern Sie die Änderungen in der Datei „UIMap.Designer“, indem Sie **Speichern** auf der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Symbolleiste wählen.  
  
 *Was sollte ich noch wissen?*  
 **Häufige Probleme**  
  
- ![Symbol „Warnung“](../test/media/caution.gif "caution") **Warnung:** Wenn eine Methode aufgeteilt wird, müssen Sie den Code ändern, mit dem die vorhandene Methode aufgerufen wird, damit die neue erstellte Methode auch aufgerufen wird, falls Sie die enthaltenen UI-Aktionen weiterhin benötigen. Beim Aufteilen einer Methode wird ein Microsoft Visual Studio-Dialogfeld angezeigt. In diesem werden Sie darauf hingewiesen, dass Sie jeglichen Code ändern müssen, mit dem die vorhandene Methode aufgerufen wird, damit die neue Methode auch aufgerufen wird. Klicken Sie auf **Ja**.  
  
  **Tipps**  
  
- ![Tipp](../test/media/tip.png "Tip") Wählen Sie zum Rückgängigmachen der Aufteilung **Rückgängig** im Menü **Bearbeiten** aus, oder drücken Sie STRG+Z.  
  
- ![Tipp](../test/media/tip.png "Tip") Sie können die neue Methode umbenennen. Wählen Sie sie im Bereich „UI-Aktionen“, und wählen Sie die Schaltfläche **Umbenennen** in der Symbolleiste des Editors für Tests der programmierten UI.  
  
   - oder -   
  
   Öffnen Sie das Kontextmenü für die neue Testmethode, und wählen Sie **Umbenennen**.  
  
   Ein Microsoft Visual Studio-Dialogfeld wird angezeigt. In diesem werden Sie darauf hingewiesen, dass Sie jeglichen Code ändern müssen, der auf die Methode verweist. Klicken Sie auf **Ja**.  
  
##  <a name="CodedUITestEditor_MoveMethods"></a> Eine Testmethode in die UIMap-Datei verschieben, um Anpassungen zu vereinfachen  
 Wenn Sie feststellen, dass eine der Testmethoden im Test der programmierten UI benutzerdefinierten Code erfordert, müssen Sie sie in die Datei „UIMap.cs“ oder „UIMap.vb“ verschieben. Andernfalls wird der Code beim erneuten Kompilieren des Tests der programmierten UI überschrieben. Wenn Sie die Methode nicht verschieben, wird der benutzerdefinierte Code bei jedem erneuten Kompilieren des Tests überschrieben.  
  
 Wählen Sie im Bereich **UI-Aktion** die Testmethode aus, die Sie in die Datei "UIMap.cs" oder "UIMap.vb" verschieben möchten. Dadurch vereinfachen Sie die Funktion für benutzerdefinierten Code, die beim erneuten Kompilieren des Tests nicht überschrieben wird. Wählen Sie als Nächstes die Schaltfläche **Code verschieben** auf der Symbolleiste des Editors für Tests der programmierten UI, oder öffnen Sie das Kontextmenü für die Testmethode und wählen **Code verschieben**aus. Die Testmethode wird aus der UIMap.uitest-Datei entfernt und nicht mehr im Bereich der UI-Aktionen angezeigt. Öffnen Sie zum Bearbeiten der verschobenen Testdatei die Datei „UIMap.cs“ oder „UIMap.vb“ im Projektmappen-Explorer.  
  
 Wenn Sie das Verschieben der Methode abgeschlossen haben, speichern Sie die Änderungen in der Datei „UIMap.Designer“, indem Sie **Speichern** auf der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Symbolleiste wählen.  
  
 *Was sollte ich noch wissen?*  
 **Häufige Probleme**  
  
- ![Symbol „Warnung“](../test/media/caution.gif "caution") **Warnung:** Nach dem Verschieben einer Methode kann sie mit dem Editor für Tests der programmierten UI nicht mehr bearbeitet werden. Sie müssen den benutzerdefinierten Code hinzufügen und ihn mit dem Code-Editor verwalten. Beim Verschieben einer Methode wird ein Microsoft Visual Studio-Dialogfeld angezeigt. Sie werden darauf hingewiesen, dass die Methode aus der Datei „UIMap.uitest“ in die Datei „UIMap.cs“ oder „UIMap.vb“ verschoben wird, und dass die Methode mit dem Editor für Tests der programmierten UI nicht mehr bearbeitet werden kann. Klicken Sie auf **Ja**.  
  
  **Tipps**  
  
- ![Tipp](../test/media/tip.png "Tip") Wählen Sie zum Rückgängigmachen der Verschiebung **Rückgängig** im Menü **Bearbeiten** aus, oder drücken Sie STRG+Z. Allerdings müssen Sie den Code dann manuell aus der Datei „UIMap.cs“ oder „UIMap.vb“ entfernen.  
  
##  <a name="CodedUITestEditor_LocateUIControl"></a> Suchen eines UI-Steuerelements in der getesteten Anwendung  
 Manchmal kann die Darstellung der Position der Steuerelemente in der Benutzeroberfläche der getesteten Anwendung schwierig sein. Zu den Funktionen des Editors für Tests der programmierten UI zählen die Möglichkeiten zum Auswählen eines Steuerelements, das in der UI-Steuerelementzuordnung aufgeführt ist, und zum Anzeigen der Position in der getesteten Anwendung. Mit der Funktion **UI-Steuerelemente suchen** in der getesteten Anwendung können auch Änderungen der Sucheigenschaften überprüft werden, die an einem Steuerelement vorgenommen wurden.  
  
 ![UI-Steuerelement suchen](../test/media/codeduilocatecontrol.png "CodedUILocateControl")  
  
 ![Steuerelement wird in der Anwendung getestet](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")  
  
 Wählen Sie im Bereich **UI-Steuerelementzuordnung** das Steuerelement aus, das Sie in der Anwendung mit dem Test suchen möchten. Öffnen Sie das Kontextmenü für das Steuerelement, und wählen Sie dann **UI-Steuerelement suchen**. In der Anwendung, die getestet wird, ist das Steuerelement mit einem blauen Rahmen markiert.  
  
 *Was sollte ich noch wissen?*  
 **Häufige Probleme**  
  
- ![Symbol „Warnung](../test/media/caution.gif "caution") **Warnung:** Stellen Sie vor dem Suchen eines UI-Steuerelements sicher, dass die Anwendung mit dem Test ausgeführt wird.  
  
  **Tipps**  
  
- ![Tipp](../test/media/tip.png "Tip") Sie können auch die Option **Alle suchen** verwenden, um zu überprüfen, ob die Position aller Steuerelemente in einem Container korrekt ermittelt werden kann. Diese Option wird im nächsten Abschnitt beschrieben.  
  
##  <a name="CodedUITestEditor_LocateDecendants"></a> Suchen eines Steuerelements und seiner Nachfolgerelemente  
 Sie können überprüfen, ob alle Steuerelemente in einem Container in der Benutzeroberfläche der getesteten Anwendung ordnungsgemäß ermittelt werden können. Dies kann bei der Überprüfung von Sucheigenschaftenänderungen hilfreich sein, die möglicherweise am Container vorgenommen wurden. Außerdem können Sie bei umfangreichen Änderungen an der Benutzeroberfläche der getesteten Anwendung überprüfen, ob die vorhandenen Eigenschaften für die Steuerelementsuche weiterhin korrekt sind.  
  
 ![Alle untergeordneten Steuerelemente suchen](../test/media/codeduilocateall.png "CodedUILocateAll")  
  
 ![Alle Steuerelemente gefunden](../test/media/codeduilocateall2.png "CodedUILocateAll2")  
  
 Wählen Sie im Bereich **UI-Steuerelementzuordnung** das Containersteuerelement aus, das Sie suchen möchten und für das Sie alle Nachfolgerelemente anzeigen möchten. Öffnen Sie das Kontextmenü für das Steuerelement, und wählen Sie dann **Alle suchen**. Das Containersteuerelement und alle Nachfolgersteuerelemente sind entweder mit einem grünen Häkchen oder einem roten „X“ im Editor für Tests der programmierten UI markiert. Anhand dieser Markierungen sehen Sie, ob die Steuerelemente in der getesteten Anwendung erfolgreich ermittelt werden konnten.  
  
 *Was sollte ich noch wissen?*  
 **Häufige Probleme**  
  
-   ![Symbol „Warnung“](../test/media/caution.gif "caution") **Warnung:** Stellen Sie vor dem Suchen der UI-Steuerelemente sicher, dass die Anwendung mit dem Test ausgeführt wird.  
  
##  <a name="CodedUITestEditor_InsertDelay"></a> Einfügen einer Verzögerung vor einer UI-Aktion  
 Gelegentlich soll der Test möglicherweise auf bestimmte Ereignisse warten, z. B. das Anzeigen eines Fensters, das Ausblenden einer Statusleiste usw. Mit dem Editor für Tests der programmierten UI können Sie zu diesem Zweck vor einer UI-Aktion eine Verzögerung einfügen. Sie können angeben, wie viele Sekunden die Verzögerung dauern soll.  
  
 ![Verzögerung vor UI-Aktion einfügen](../test/media/codeduidelay.png "CodedUIDelay")  
  
 ![Verzögerung mit 5 Sekunden hinzugefügt](../test/media/codeduidealy2.png "CodedUIDealy2")  
  
 Erweitern Sie im Bereich **UI-Aktion** die Testmethode mit der UI-Aktion, vor die Sie eine Verzögerung einfügen möchten. Wählen Sie die UI-Aktion aus. Öffnen Sie das Kontextmenü für die UI-Aktion, und wählen Sie **Verzögerung einfügen vor**. Eine Verzögerung wird vor der ausgewählten UI-Aktion mit dem folgenden Text eingefügt und hervorgehoben: **1 Sekunde auf Benutzerverzögerungen zwischen Aktionen warten**. Ändern Sie im Fenster „Eigenschaften“ den Wert für die Eigenschaft **Verzögerung** auf die gewünschte Anzahl von Millisekunden.  
  
 Wenn Sie das Einfügen der Verzögerung abgeschlossen haben, speichern Sie die Änderungen in der Datei „UIMap.Designer“, indem Sie **Speichern** auf der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Symbolleiste wählen.  
  
 *Was sollte ich noch wissen?*  
 **Notizen**  
  
- ![Erforderliche Komponente](../test/media/prereq.png "Prereq") Wenn ein bestimmtes Steuerelement vor einer UI-Aktion verfügbar sein muss, sollten Sie mit der entsprechenden UITestControl.WaitForControlXXX-Methode ggf. benutzerdefinierten Code zur Testmethode hinzufügen. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Festlegen, dass bei Wiedergabe von Tests der programmierten UI auf bestimmte Ereignisse gewartet wird](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)  
  
  **Tipps**  
  
- ![Tipp](../test/media/tip.png "Tip") Wenn das Fenster „Eigenschaften“ nicht angezeigt wird, halten Sie ALT gedrückt und drücken Sie EINGABE, oder drücken Sie alternativ F4.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="guidance"></a>Empfehlungen  
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="faq"></a>FAQ  
 [Tests der codierten UI – FAQ 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Tests der codierten UI – FAQ 2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio UI Automation Testing (includes CodedUI) (Tests der Benutzeroberflächenautomatisierung (einschließlich programmierte UI) in Visual Studio)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)   
 [Erstellen von Tests der codierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Erstellen eines datengesteuerten Tests der programmierten UI](../test/creating-a-data-driven-coded-ui-test.md)   
 [Generieren eines Tests der programmierten UI aus einer vorhandenen Aktionsaufzeichnung](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)   
 [Exemplarische Vorgehensweise: Erstellen, Bearbeiten und Verwalten von Tests der programmierten UI](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)



