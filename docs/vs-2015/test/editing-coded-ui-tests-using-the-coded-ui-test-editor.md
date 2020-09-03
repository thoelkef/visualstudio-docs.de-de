---
title: Bearbeiten von Tests der programmierten UI mithilfe des Editors für Tests der programmierten UI | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c070f1bafb157e3979eb9c1f49b317b17807f1e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "82587003"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Bearbeiten von Tests der programmierten UI mithilfe des Editors für Tests der programmierten UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Editor für Tests der programmierten UI können Sie Tests der programmierten UI mühelos ändern. Er ermöglicht das Suchen, Anzeigen und Bearbeiten von Eigenschaften der Testmethoden und UI-Aktionen. Darüber hinaus können Sie mit der UI-Steuerelementzuordnung die entsprechenden Steuerelemente anzeigen und bearbeiten.

 **Anforderungen**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Warum sollte ich das tun?
 Mit dem Editor für Tests der programmierten UI sind Sie schneller und effizienter, als wenn Sie den Code in den Testmethoden der programmierten UI mithilfe des Code-Editors bearbeiten. Mit dem Editor für Tests der programmierten UI können Sie mithilfe der Symbolleiste und der Kontextmenüs schneller die den UI-Aktionen und -Steuerelementen zugeordneten Eigenschaftswerte finden und bearbeiten. Mit der Symbolleiste des Editors für Tests der programmierten UI können Sie beispielsweise die folgenden Befehle ausführen:

 ![UI-Test-Editor](../test/media/uitesteditor.png "Uitesteditor")

1. Mit [Suchen](../ide/finding-and-replacing-text.md) können Sie nach UI-Aktionen und -Steuerelementen suchen.

2. Mit[Löschen](#CodedUITestEditor_DeleteUIActions) können Sie unerwünschte UI-Aktionen entfernen.

3. Mit**Umbenennen** können Sie die Namen für Testmethoden und Steuerelemente ändern.

4. **Eigenschaften** Öffnet das Fenster Eigenschaften für das ausgewählte Element.

5. Mit[In eine neue Methode aufteilen](#CodedUITestEditor_SplitMethods) können Sie UI-Aktionen modularisieren.

6. Mit[Code verschieben](#CodedUITestEditor_MoveMethods) können Sie benutzerdefinierten Code zu Testmethoden  hinzufügen.

7. Mit[Verzögerung einfügen vor](#CodedUITestEditor_InsertDelay) können Sie eine Pause in Millisekunden vor einer UI-Aktion hinzufügen.

8. Mit[UI-Steuerelement suchen](#CodedUITestEditor_LocateUIControl) wird die Position des Steuerelements in der Benutzeroberfläche der getesteten Anwendung ermittelt.

9. " [Alle suchen](#CodedUITestEditor_LocateDecendants) " unterstützt Sie bei der Überprüfung der Steuerungs Eigenschaft und erheblicher Änderungen an den Steuerelementen der Anwendung

## <a name="how-do-i-do-this"></a>Wie geht das?
 Beim Öffnen der Datei „UIMap.uitest“ in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], die mit dem Test der programmierten UI im Testprojekt der programmierten UI verbunden ist, wird der Test der programmierten UI automatisch im Editor für Tests der programmierten UI angezeigt. In den folgenden Verfahren wird beschrieben, wie Sie mithilfe der Symbolleiste und den Kontextmenüs des Editors die Testmethoden, Eigenschaften für die UI-Aktionen und Steuerelemente finden und bearbeiten können.

## <a name="open-a-coded-ui-test"></a>Einen Test der codierten UI öffnen
 Mit dem Editor für Tests der programmierten UI können Sie den Visual C#- und Visual Basic-basierten Test der programmierten UI anzeigen und bearbeiten.

 ![Kontextmenü mit Test-Generator für codierte UI](../test/media/editcodeduitest.png "Editcodeduitest")

 Öffnen Sie in Projektmappen-Explorer das Kontextmenü für **UIMap. UITest** , und wählen Sie **Öffnen**aus. Der Test der codierten UI wird im Editor für den Test der codierten UI angezeigt. Sie können nun aufgezeichnete Methoden, Aktionen und entsprechende Steuerelemente im Test der programmierten UI anzeigen und bearbeiten.

> [!TIP]
> Beim Auswählen einer UI-Aktion, die in einer Methode im Bereich **UI-Aktionen** enthalten ist, wird das entsprechende Steuerelement hervorgehoben. Sie können auch die UI-Aktion oder die Steuerelementeigenschaften ändern.

 Der Editor für Tests der programmierten UI*wird nicht angezeigt* .
Möglicherweise verwenden Sie eine Version von Visual Studio Enterprise, die älter als 2012 ist. Der Editor für Tests der programmierten UI stand auch in Visual Studio 2010 Feature Pack 2 mit einem MSDN-Abonnement zur Verfügung. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Microsoft Visual Studio 2010 Feature Pack 2](https://msdn.microsoft.com/library/gg269474.aspx).

## <a name="modify-ui-action-properties-and-their-corresponding-control-properties"></a><a name="CodedUITestEditor_EditActionAndControlProperties"></a> Eigenschaften der UI-Aktionen und ihre entsprechenden Steuerelementeigenschaften ändern
 Mit dem Editor für Tests der programmierten UI, können Sie leicht alle UI-Aktionen in den Testmethoden finden und anzeigen. Wenn Sie die UI-Aktion im Editor auswählen, wird das entsprechende Steuerelement automatisch hervorgehoben. Wenn Sie ein Steuerelement auswählen, werden entsprechend die zugeordneten UI-Aktionen hervorgehoben. Wenn Sie eine UI-Aktion oder ein -Steuerelement auswählen, können Sie dann einfach das Fenster „Eigenschaften“ verwenden, um die entsprechenden Eigenschaften zu  ändern.

 ![Eigenschaften der UI-Aktion](../test/media/codeduiedituiaction.png "Codeduiedituiaction") Eigenschaften der UI-Aktion bearbeiten

 Erweitern Sie zum Ändern der Eigenschaften einer UI-Aktion die Testmethode im Bereich **UI-Aktion** , die die UI-Aktion mit den zu bearbeitenden Eigenschaften enthält. Wählen Sie die UI-Aktion aus, und ändern Sie dann die Eigenschaften im Fenster „Eigenschaften“.

 Wenn z. b. ein Server nicht verfügbar ist und Sie eine UI-Aktion mit dem Webbrowser verknüpft haben, die besagt, dass Sie **zur Webseite <http://Contoso1/default.aspx’> **wechseln, können Sie die URL in ändern `‘http://Contoso2/default.aspx’` .

 ![Steuerelement Eigenschaften](../test/media/codeduitestcontrolprop.png "Codeduitestcontrolprop") Bearbeiten von Steuerelement Eigenschaften

 Die Änderung der Eigenschaften eines Steuerelements erfolgt auf die gleiche Weise wie die der UI-Aktionen. Wählen Sie im Bereich **UI-Steuerelementzuordnung** das zu bearbeitende Steuerelement aus, und bearbeiten Sie seine Eigenschaften im Fenster Eigenschaften.

 Ein Entwickler kann z. b. die **(ID)** -Eigenschaft auf einem Schaltflächen-Steuerelement im Quellcode für die getestete Anwendung von "idsubmit" in "idlogin" geändert haben. Wenn die **(ID)** -Eigenschaft in der Anwendung geändert wurde, kann der Test der programmierten UI nicht das Schaltflächen-Steuerelement finden, und es wird ein Fehler ausgegeben. In diesem Fall kann der Tester die Auflistung **Sucheigenschaften** öffnen und die **ID** -Eigenschaft auf den neuen Wert festlegen, den der Entwickler in der Anwendung verwendet hat. Der Tester kann auch den Eigenschafts Wert für Anzeige **Name** von "Submit" in "Login" ändern. Durch diese Änderung wird die zugeordnete UI-Aktion im Editor für Tests der programmierten UI von „Schaltfläche 'Submit' auswählen“ in „Schaltfläche 'Login' auswählen" geändert.

 Nachdem Sie die Änderungen abgeschlossen haben, speichern Sie die Änderungen in der Datei „UIMap.Designer“, indem Sie auf der **-Symbolleiste** Speichern [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auswählen.

 *Was sollte ich noch wissen?*
 **Chti**

- ![Tipp](../test/media/tip.png "Tipp") Wenn das Eigenschaftenfenster nicht angezeigt wird, halten Sie **alt** gedrückt, während Sie die **Eingabe**Taste drücken, oder drücken Sie alternativ **F4**.

- ![Tipp](../test/media/tip.png "Tipp") Wenn Sie die vorgenommenen Eigenschaften Änderungen rückgängig machen möchten, wählen Sie **Rückgängig** im Menü **Bearbeiten** aus, oder drücken Sie STRG + Z.

- ![Tipp](../test/media/tip.png "Tipp") Sie können die Schaltfläche **Suchen** auf der Symbolleiste des Editors für Tests der programmierten UI verwenden, um das Tool suchen und ersetzen in Visual Studio zu öffnen. Anschließend können Sie mit dem Steuerelement „Suchen“ nach einer UI-Aktion im Editor für Tests der programmierten UI suchen. Sie können z. B. die Option „Auf die Schaltfläche 'Anmelden' klicken“ suchen. Dies kann bei umfangreichen Tests hilfreich sein. Beachten Sie, dass Sie die Ersetzungsfunktion nicht im Tool zum Suchen und Ersetzen im Editor für Tests der programmierten UI verwenden können. Weitere Informationen finden Sie unter „Steuerelement ‚Suchen‘“ in [Finding and Replacing Text](../ide/finding-and-replacing-text.md).

- ![Tipp](../test/media/tip.png "Tipp") Manchmal kann es schwierig sein, den Speicherort der Steuerelemente in der Benutzeroberfläche der getesteten Anwendung zu visualisieren. Zu den Funktionen des Editors für Tests der programmierten UI zählen die Möglichkeiten zum Auswählen eines Steuerelements, das in der UI-Steuerelementzuordnung aufgeführt ist, und zum Anzeigen der Position in der getesteten Anwendung. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Suchen eines UI-Steuerelements in der getesteten Anwendung](#CodedUITestEditor_LocateUIControl) im weiteren Verlauf dieses Themas.

- ![Tipp](../test/media/tip.png "Tipp") Möglicherweise muss das Container Steuerelement, das das Steuerelement enthält, das Sie bearbeiten möchten, erweitert werden. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Suchen eines Steuerelements und seiner Nachfolgerelemente](#CodedUITestEditor_LocateDecendants) im weiteren Verlauf dieses Themas.

## <a name="delete-unwanted-ui-actions"></a><a name="CodedUITestEditor_DeleteUIActions"></a> Unerwünschte UI-Aktionen löschen
 Sie können unerwünschte UI-Aktionen in dem Test der programmierten UI leicht entfernen.

 ![UI-Aktion löschen](../test/media/codeduideleteuiaction.png "Codeduideleteuiaction")

 Erweitern Sie im Bereich **UI-Aktion** die Testmethode, die die zu löschende UI-Aktion enthält. Öffnen Sie das Kontextmenü für die UI-Aktion, und wählen Sie dann **Löschen**.

## <a name="split-a-test-method-into-two-separate-methods"></a><a name="CodedUITestEditor_SplitMethods"></a> Eine Testmethode in zwei separate Methoden aufteilen
 Sie können eine Testmethode aufteilen, um die UI-Aktionen zu optimieren und zu modularisieren. Beispielsweise kann der Test eine einzelne Testmethode mit UI-Aktionen in zwei Containersteuerelementen beinhalten. Die UI-Aktionen werden ggf. besser in zwei Methoden modularisiert, die einem Container entsprechen.

 ![Teilen einer Testmethode](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")

 ![Zwei Testmethoden](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")

 Erweitern Sie im Bereich **UI-Aktion** die Testmethode, die Sie in zwei separate Methoden aufteilen möchten, und wählen Sie die UI-Aktion, die als Anfang der neuen Testmethode dienen soll. Öffnen Sie entweder das Kontextmenü für die UI-Aktion, und wählen Sie dann **In eine neue Methode aufteilen**, oder wählen Sie die Schaltfläche **In eine neue Methode aufteilen** auf der Symbolleiste des Editors für Tests der programmierten UI. Die neue Testmethode wird im Bereich „UI-Aktionen“ angezeigt. Sie enthält UI-Aktionen, beginnend mit der Aktion, in der Sie die Aufteilung angegeben haben.

 Wenn Sie die Aufteilung der Methode abgeschlossen haben, speichern Sie die Änderungen in der Datei „UIMap.Designer“, indem Sie **Speichern** auf der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Symbolleiste wählen.

 *Was sollte ich noch wissen?*
 **Häufige Probleme**

- Warn ![Symbol](../test/media/caution.gif "caution") **Warnung:** Wenn Sie eine Methode aufteilen, müssen Sie jeden Code ändern, der die vorhandene Methode aufruft, um auch die neue Methode aufzurufen, die Sie gerade erstellen möchten, wenn Sie diese UI-Aktionen weiterhin benötigen. Beim Aufteilen einer Methode wird ein Microsoft Visual Studio-Dialogfeld angezeigt. In diesem werden Sie darauf hingewiesen, dass Sie jeglichen Code ändern müssen, mit dem die vorhandene Methode aufgerufen wird, damit die neue Methode auch aufgerufen wird. Klicken Sie auf **Ja**.

  **Tipps**

- ![Tipp](../test/media/tip.png "Tipp") Um die Aufteilung rückgängig zu machen, wählen Sie **Rückgängig** im Menü **Bearbeiten** aus, oder drücken Sie STRG + Z.

- ![Tipp](../test/media/tip.png "Tipp") Sie können die neue Methode umbenennen. Wählen Sie sie im Bereich UI-Aktionen aus, und wählen Sie die Schaltfläche **Umbenennen** in der Symbolleiste des Editors für Tests der programmierten UI aus.

   - oder -

   Öffnen Sie das Kontextmenü für die neue Testmethode, und wählen Sie **Umbenennen**.

   Ein Microsoft Visual Studio-Dialogfeld wird angezeigt. In diesem werden Sie darauf hingewiesen, dass Sie jeglichen Code ändern müssen, der auf die Methode verweist. Klicken Sie auf **Ja**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a><a name="CodedUITestEditor_MoveMethods"></a> Verschieben einer Testmethode in die UIMap-Datei, um Anpassungen zu vereinfachen
 Wenn Sie feststellen, dass eine der Testmethoden im Test der programmierten UI benutzerdefinierten Code erfordert, müssen Sie sie in die Datei „UIMap.cs“ oder „UIMap.vb“ verschieben. Andernfalls wird der Code beim erneuten Kompilieren des Tests der programmierten UI überschrieben. Wenn Sie die Methode nicht verschieben, wird der benutzerdefinierte Code bei jedem erneuten Kompilieren des Tests überschrieben.

 Wählen Sie im Bereich **UI-Aktion** die Testmethode aus, die Sie in die UIMap.cs-oder UIMap. vb-Datei verschieben möchten, um benutzerdefinierte Code Funktionen zu ermöglichen, die nicht überschrieben werden, wenn der Testcode neu kompiliert wird. Wählen Sie als Nächstes die Schaltfläche **Code verschieben** auf der Symbolleiste des Editors für Tests der programmierten UI, oder öffnen Sie das Kontextmenü für die Testmethode und wählen **Code verschieben**aus. Die Testmethode wird aus der UIMap.uitest-Datei entfernt und nicht mehr im Bereich der UI-Aktionen angezeigt. Öffnen Sie zum Bearbeiten der verschobenen Testdatei die Datei „UIMap.cs“ oder „UIMap.vb“ im Projektmappen-Explorer.

 Wenn Sie das Verschieben der Methode abgeschlossen haben, speichern Sie die Änderungen in der Datei „UIMap.Designer“, indem Sie **Speichern** auf der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Symbolleiste wählen.

 *Was sollte ich noch wissen?*
 **Häufige Probleme**

- Warn ![Symbol](../test/media/caution.gif "caution") **Warnung:** nachdem Sie eine Methode verschoben haben, können Sie Sie nicht mehr mit dem Test-Editor für codierte UI bearbeiten. Sie müssen den benutzerdefinierten Code hinzufügen und ihn mit dem Code-Editor verwalten. Beim Verschieben einer Methode wird ein Microsoft Visual Studio-Dialogfeld angezeigt. Sie werden darauf hingewiesen, dass die Methode aus der Datei „UIMap.uitest“ in die Datei „UIMap.cs“ oder „UIMap.vb“ verschoben wird, und dass die Methode mit dem Editor für Tests der programmierten UI nicht mehr bearbeitet werden kann. Klicken Sie auf **Ja**.

  **Tipps**

- ![Tipp](../test/media/tip.png "Tipp") Um die Verschiebung rückgängig zu machen, wählen Sie **Rückgängig** im Menü **Bearbeiten** aus, oder drücken Sie STRG + Z. Allerdings müssen Sie den Code dann manuell aus der Datei „UIMap.cs“ oder „UIMap.vb“ entfernen.

## <a name="locating-a-ui-control-in-the-application-under-test"></a><a name="CodedUITestEditor_LocateUIControl"></a> Suchen eines UI-Steuer Elements in der getesteten Anwendung
 Manchmal kann die Darstellung der Position der Steuerelemente in der Benutzeroberfläche der getesteten Anwendung schwierig sein. Zu den Funktionen des Editors für Tests der programmierten UI zählen die Möglichkeiten zum Auswählen eines Steuerelements, das in der UI-Steuerelementzuordnung aufgeführt ist, und zum Anzeigen der Position in der getesteten Anwendung. Mit der Funktion **UI-Steuerelemente suchen** in der getesteten Anwendung können auch Änderungen der Sucheigenschaften überprüft werden, die an einem Steuerelement vorgenommen wurden.

 ![UI-Steuerelement suchen](../test/media/codeduilocatecontrol.png "Codeduilocatcher econtrol")

 ![Steuerelement in Anwendung-unter-Test](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")

 Wählen Sie im Bereich **UI-Steuerelementzuordnung** das Steuerelement aus, das Sie in der Anwendung mit dem Test suchen möchten. Öffnen Sie das Kontextmenü für das Steuerelement, und wählen Sie dann **UI-Steuerelement suchen**. In der Anwendung, die getestet wird, ist das Steuerelement mit einem blauen Rahmen markiert.

 *Was sollte ich noch wissen?*
 **Häufige Probleme**

- Warn ![Symbol](../test/media/caution.gif "caution") **Warnung:** Vergewissern Sie sich vor dem Auffinden eines UI-Steuer Elements, dass die Anwendung, die dem Test zugeordnet ist, ausgeführt wird.

  **Chti**

- ![Tipp](../test/media/tip.png "Tipp") Wahlweise können Sie auch die Option **Alle suchen** verwenden, um zu überprüfen, ob alle Steuerelemente in einem Container ordnungsgemäß gefunden werden können. Diese Option wird im nächsten Abschnitt beschrieben.

## <a name="locating-a-control-and-its-descendants"></a><a name="CodedUITestEditor_LocateDecendants"></a> Suchen eines Steuer Elements und seiner Nachfolger Elemente
 Sie können überprüfen, ob alle Steuerelemente in einem Container in der Benutzeroberfläche der getesteten Anwendung ordnungsgemäß ermittelt werden können. Dies kann bei der Überprüfung von Sucheigenschaftenänderungen hilfreich sein, die möglicherweise am Container vorgenommen wurden. Außerdem können Sie bei umfangreichen Änderungen an der Benutzeroberfläche der getesteten Anwendung überprüfen, ob die vorhandenen Eigenschaften für die Steuerelementsuche weiterhin korrekt sind.

 ![Alle untergeordneten Steuerelemente suchen](../test/media/codeduilocateall.png "Codeduilocateall")

 ![Alle Steuerelemente gefunden](../test/media/codeduilocateall2.png "CodedUILocateAll2")

 Wählen Sie im Bereich **UI-Steuerelementzuordnung** das Containersteuerelement aus, das Sie suchen möchten und für das Sie alle Nachfolgerelemente anzeigen möchten. Öffnen Sie das Kontextmenü für das Steuerelement, und wählen Sie dann **Alle suchen**. Das Containersteuerelement und alle Nachfolgersteuerelemente sind entweder mit einem grünen Häkchen oder einem roten „X“ im Editor für Tests der programmierten UI markiert. Anhand dieser Markierungen sehen Sie, ob die Steuerelemente in der getesteten Anwendung erfolgreich ermittelt werden konnten.

 *Was sollte ich noch wissen?*
 **Häufige Probleme**

- Warn ![Symbol](../test/media/caution.gif "caution") **Warnung:** Vergewissern Sie sich vor dem Suchen der UI-Steuerelemente, dass die Anwendung, die dem Test zugeordnet ist, ausgeführt wird.

## <a name="inserting-a-delay-before-a-ui-action"></a><a name="CodedUITestEditor_InsertDelay"></a> Einfügen einer Verzögerung vor einer UI-Aktion
 Gelegentlich soll der Test möglicherweise auf bestimmte Ereignisse warten, z. B. das Anzeigen eines Fensters, das Ausblenden einer Statusleiste usw. Mit dem Editor für Tests der programmierten UI können Sie zu diesem Zweck vor einer UI-Aktion eine Verzögerung einfügen. Sie können angeben, wie viele Sekunden die Verzögerung dauern soll.

 ![Verzögerung vor UI-Aktion einfügen](../test/media/codeduidelay.png "Codeduidelay")

 ![Verzögerung mit 5 Sekunden hinzugefügt](../test/media/codeduidealy2.png "CodedUIDealy2")

 Erweitern Sie im Bereich **UI-Aktion** die Testmethode mit der UI-Aktion, vor die Sie eine Verzögerung einfügen möchten. Wählen Sie die UI-Aktion aus. Öffnen Sie das Kontextmenü für die UI-Aktion, und wählen Sie **Verzögerung einfügen vor**. Eine Verzögerung wird vor der ausgewählten UI-Aktion mit dem folgenden Text eingefügt und hervorgehoben: **1 Sekunde auf Benutzerverzögerungen zwischen Aktionen warten**. Ändern Sie im Fenster Eigenschaften den Wert für die Eigenschaft **Verzögerung** auf die gewünschte Anzahl von Millisekunden.

 Wenn Sie das Einfügen der Verzögerung abgeschlossen haben, speichern Sie die Änderungen in der Datei „UIMap.Designer“, indem Sie **Speichern** auf der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Symbolleiste wählen.

 *Was sollte ich noch wissen?*
 **Notizen**

- ![Prerequsite](../test/media/prereq.png "Prereq") Wenn Sie sicherstellen müssen, dass ein bestimmtes Steuerelement vor einer UI-Aktion verfügbar ist, sollten Sie mit der entsprechenden UITestControl. waitforcontrolxxx ()-Methode benutzerdefinierten Code zur Testmethode hinzufügen. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Festlegen, dass bei Wiedergabe von Tests der programmierten UI auf bestimmte Ereignisse gewartet wird](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)

  **Chti**

- ![Tipp](../test/media/tip.png "Tipp") Wenn das Eigenschaftenfenster nicht angezeigt wird, halten Sie ALT gedrückt, während Sie die EINGABETASTE drücken, oder drücken Sie alternativ F4.

## <a name="external-resources"></a>Externe Ressourcen

### <a name="guidance"></a>Anleitungen
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="faq"></a>Häufig gestellte Fragen
 [Tests der codierten UI – FAQ 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Tests der codierten UI – FAQ 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Forum
 [Tests der Benutzeroberflächenautomatisierung (einschließlich programmierte UI) in Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Weitere Informationen
 [Verwenden von Benutzeroberflächen Automatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md) [Erstellen von Tests](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) der programmierten UI [Erstellen eines datengesteuerten](../test/creating-a-data-driven-coded-ui-test.md) Tests der programmierten UI Erstellen eines Tests der programmierten UI [aus einer vorhandenen Aktions Aufzeichnung Exemplarische Vorgehensweise](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [: erstellen, bearbeiten und Verwalten eines Tests](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md) der programmierten UI
