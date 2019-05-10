---
title: 'Schritt 5: Hinzufügen von Steuerelementen zum Formular | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e05e8c313e6c2345964386c9c4f08c1bb6f16089
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442559"
---
# <a name="step-5-add-controls-to-your-form"></a>Schritt 5: Hinzufügen von Steuerelementen zum Formular
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Schritt fügen Sie dem Formular Steuerelemente hinzu, z. B. ein `PictureBox`-Steuerelement und ein `CheckBox`-Steuerelement. Danach fügen Sie dem Formular Schaltflächen hinzu.  
  
 ![Link zum Video](../data-tools/media/playvideo.gif "PlayVideo")eine Videoversion dieses Themas finden Sie unter [Tutorial 1: Erstellen eines Bildanzeigeprogramms in Visual Basic - Video 2](http://go.microsoft.com/fwlink/?LinkId=205211) oder [Lernprogramm 1: Erstellen eines Bildanzeigeprogramms in C# -Video 2](http://go.microsoft.com/fwlink/?LinkId=205200). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.  
  
### <a name="to-add-controls-to-your-form"></a>So fügen Sie dem Formular ein Steuerelement hinzu  
  
1. Wechseln Sie zur Registerkarte „Toolbox“ (gleich links vom Visual Studio-IDE), und klappen Sie die Gruppe **Allgemeine Steuerelemente** auf. In dieser Gruppe werden allgemeine Steuerelemente angezeigt, die in Formularen häufig verwendet werden.  
  
2. Wählen Sie das TableLayoutPanel-Steuerelement auf dem Formular aus. Um zu überprüfen, dass das TableLayoutPanel-Steuerelement ausgewählt ist, stellen Sie sicher, dass der Name im Dropdown-Listenfeld oben im Fenster **Eigenschaften** angezeigt wird. Sie können Formularsteuerelemente auch mithilfe des Dropdown-Listenfelds oben im Fenster **Eigenschaften** auswählen. Diese Form der Steuerelementauswahl kann häufig einfacher sein als das Auswählen eines kleinen Steuerelements mit der Maus.  
  
3. Doppelklicken Sie auf das Element **PictureBox**, um dem Formular ein PictureBox-Steuerelement hinzuzufügen. Da TableLayoutPanel angedockt ist, um das Formular zu füllen, fügt die IDE der ersten leeren Zelle (der oberen linken Ecke) das PictureBox-Steuerelement hinzu.  
  
4. Wählen Sie das neue PictureBox-Steuerelement aus, und wählen Sie dann das schwarze Dreieck auf dem neuen PictureBox-Steuerelement aus, um die dazugehörige Aufgabenliste anzuzeigen, wie im folgenden Bild dargestellt.  
  
     ![PictureBox-Aufgaben](../ide/media/express-pictureboxtasks.png "Express_PictureBoxAufgaben")  
PictureBox-Aufgaben  
  
    > [!NOTE]
    > Wenn Sie dem TableLayoutPanel unbeabsichtigt den falschen Typ von Steuerelement hinzufügen, können Sie es löschen. Klicken Sie mit der rechten Maustaste auf das Steuerelement, und wählen Sie dann im Kontextmenü **Löschen** aus. Sie können Steuerelemente aus dem Formular auch mithilfe der Menüleiste entfernen. Wählen Sie in der Menüleiste **Bearbeiten**, **Rückgängig** oder **Bearbeiten**, **Löschen** aus.  
  
5. Wählen Sie den Link **In übergeordnetem Container andocken** aus. Dadurch wird die **Dock**-Eigenschaft des PictureBox-Steuerelements automatisch auf **Fill** festgelegt. Sie können dies überprüfen, indem Sie das PictureBox-Steuerelement auswählen. Öffnen Sie dann das Fenster **Eigenschaften**, und vergewissern Sie sich, dass die **Dock**-Eigenschaft auf **Fill** festgelegt ist.  
  
6. Sorgen Sie dafür, dass das PictureBox-Steuerelement beide Spalten umfasst, indem Sie dessen **ColumnSpan**-Eigenschaft ändern. Wählen Sie das PictureBox-Steuerelement aus, und legen Sie dessen Eigenschaft **ColumnSpan** auf **2** fest. Auch wenn das PictureBox-Steuerelement leer ist, möchten Sie einen leeren Frame anzeigen. Legen Sie die **BorderStyle**-Eigenschaft auf **Fixed3D** fest.  
  
    > [!NOTE]
    > Wenn die Eigenschaft **ColumnSpan** für das PictureBox-Steuerelement nicht angezeigt wird, ist es wahrscheinlich, dass das PictureBox-Steuerelement zum Formular anstatt zum TableLayoutPanel hinzugefügt wurde. Um dies zu korrigieren, wählen Sie das PictureBox-Steuerelement aus, löschen Sie es, wählen Sie das TableLayoutPanel aus, und fügen Sie dann ein neues PictureBox-Steuerelement hinzu.  
  
7. Wählen Sie das TableLayoutPanel auf dem Formular aus, und fügen Sie dann dem Formular ein **CheckBox**-Steuerelement hinzu. Doppelklicken Sie in der Toolbox auf das **CheckBox**-Element, um der nächsten freien Zelle in der Tabelle ein neues CheckBox-Steuerelement hinzuzufügen. Da ein PictureBox-Steuerelement die ersten beiden Zellen im TableLayoutPanel einnimmt, wird das CheckBox-Steuerelement der linken unteren Zelle hinzugefügt. Wählen Sie die Eigenschaft **Text** aus, und geben Sie das Wort **Stretch** ein, wie in der folgenden Abbildung dargestellt.  
  
     ![TextBox-Steuerelement mit Stretch-Eigenschaft](../ide/media/express-pictureviewercheckbox.png "Express_Bildanzeigeprogramm")  
TextBox-Steuerelement mit Stretch-Eigenschaft  
  
8. Wählen Sie das TableLayoutPanel im Formular aus, und wechseln Sie dann zur Gruppe **Container** in der Toolbox (dort, wo Sie das TableLayoutPanel-Steuerelement abgerufen haben). Doppelklicken Sie auf das **FlowLayoutPanel**-Element, um ein neues Steuerelement zur letzten Zelle im PictureBox-Steuerelement (unten rechts) hinzuzufügen. Docken Sie anschließend das FlowLayoutPanel im TableLayoutPanel an (entweder durch Auswählen von **In übergeordnetem Container andocken** in der Aufgabenliste des schwarzen Dreiecks von FlowLayoutPanel oder durch Festlegen der FlowLayoutPanel-Eigenschaft **Dock** auf **Fill**).  
  
    > [!NOTE]
    > Ein FlowLayoutPanel ist ein Container, der andere Steuerelemente in ordentlich nebeneinander anordnet. Wenn Sie die FlowLayoutPanel-Größe ändern und genügend Platz vorhanden ist, um alle Steuerelemente in einer einzelnen Zeile anzuordnen, dann geschieht das. Andernfalls ordnet es die Steuerelemente untereinander in Zeilen an. Sie verwenden einen FlowLayoutPanel-Container, der vier Schaltflächen enthält. Wenn die Schaltflächen beim Hinzufügen untereinander angeordnet werden, stellen Sie sicher, dass FlowLayoutPanel ausgewählt ist, bevor die Schaltflächen hinzugefügt werden. Obwohl bereits angemerkt wurde, dass jede Zelle nur ein Steuerelement aufnehmen kann, enthält die Zelle unten rechts von TableLayoutPanel vier Schaltflächen-Steuerelemente. Die ist möglich, da Sie in eine Zelle ein Steuerelement einfügen können, das andere Steuerelemente aufnimmt. Diese Art von Steuerelement wird als Container bezeichnet, und FlowLayoutPanel ist ein Container.  
  
### <a name="to-add-buttons"></a>So fügen Sie Schaltflächen hinzu  
  
1. Wählen Sie das neu hinzugefügte FlowLayoutPanel aus. Gehen Sie in der Toolbox zu **Allgemeine Steuerelemente**, und doppelklicken Sie auf das Element **Schaltfläche**, um dem FlowLayoutPanel ein Schaltflächen-Steuerelement namens **button1** hinzuzufügen. Wiederholen Sie den Vorgang, um eine weitere Schaltfläche hinzuzufügen. Die IDE stellt fest, dass bereits eine Schaltfläche mit dem Namen **button1** vorhanden ist, und gibt der nächsten Schaltfläche den Namen **button2**.  
  
2. In der Regel fügen Sie die anderen Schaltflächen mit der Toolbox hinzu. Wählen Sie dieses Mal **button2** und dann in der Menüleiste **Bearbeiten**, **Kopieren** aus (oder drücken Sie STRG+C). Wählen Sie in der Menüleiste **Bearbeiten**, **Einfügen** aus (oder drücken Sie STRG+V), um eine Kopie der Schaltfläche einzufügen. Fügen Sie sie jetzt erneut ein. Die IDE hat dem FlowLayoutPanel jetzt **button3** und **button4** hinzugefügt.  
  
    > [!NOTE]
    > Sie können jedes Steuerelement kopieren und einfügen. Die neuen Steuerelemente werden von der IDE auf eine logische Weise benannt und eingefügt. Wenn Sie ein Steuerelement in einen Container einfügen, wählt die IDE den nächsten logischen Platz für die Platzierung aus.  
  
3. Wählen Sie die erste Schaltfläche aus, und legen Sie die entsprechende **Text**-Eigenschaft auf **Bild anzeigen** fest. Legen Sie dann die **Text**-Eigenschaften der nächsten drei Schaltflächen auf **Bild löschen**, **Hintergrundfarbe festlegen** und **Schließen** fest.  
  
4. Der nächste Schritt ist, die Größe der Schaltflächen anzupassen und so anzuordnen, dass sie entlang der rechten Seite des Bereichs ausgerichtet sind. Wählen Sie das FlowLayoutPanel aus, und schauen Sie dessen **FlowDirection**-Eigenschaft an. Ändern Sie die Eigenschaft in **RightToLeft**. Anschließend sollten die Schaltflächen entlang der rechten Seite der Zelle ausgerichtet sein und in umgekehrter Reihenfolge angezeigt werden, sodass sich die Schaltfläche **Bild anzeigen** auf der rechten Seite befindet.  
  
    > [!NOTE]
    > Wenn die Schaltflächen immer noch in der falschen Reihenfolge angeordnet sind, können Sie die Schaltflächen innerhalb des FlowLayoutPanel ziehen, um sie in gewünschter Reihenfolge neu anzuordnen. Sie können eine Schaltfläche auswählen und sie nach links oder rechts ziehen.  
  
5. Wählen Sie die Schaltfläche **Schließen** aus. Halten Sie die STRG-TASTE gedrückt, und wählen Sie die anderen drei Schaltflächen aus, damit alle ausgewählt werden. Wenn alle Schaltflächen ausgewählt sind, wechseln Sie zum **Eigenschaftenfenster**, und verschieben Sie den Fensterinhalt nach oben bis zur **AutoSize**-Eigenschaft. Diese Eigenschaft teilt der Schaltfläche mit, die Größe automatisch zu ändern, damit der gesamte Text Platz hat. Legen Sie die Eigenschaft auf **true** fest. Die Schaltflächen sollten jetzt die richtige Größe aufweisen und in der richtigen Reihenfolge angezeigt werden. (Sofern alle vier Schaltflächen ausgewählt sind, können Sie alle vier **AutoSize**-Eigenschaften gleichzeitig ändern.) Das folgende Bild zeigt die vier Schaltflächen an.  
  
     ![Bildanzeigeprogramm mit vier Schaltflächen](../ide/media/express-autosize.png "Express_AutoSize")  
Bildanzeigeprogramm mit vier Schaltflächen  
  
6. Führen Sie jetzt das Programm aus, um das Formular mit dem neuen Layout anzuzeigen. Noch ruft das Auswählen der Schaltflächen und des Kontrollkästchens keine Reaktion hervor, aber das ändert sich bald.  
  
### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben  
  
- Den nächsten Schritt des Tutorials finden Sie unter [Schritt 6: Benennen der Schaltflächen-Steuerelemente](../ide/step-6-name-your-button-controls.md).  
  
- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 4: Erstellen des Layouts für das Formular mit einem TableLayoutPanel-Steuerelement](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
