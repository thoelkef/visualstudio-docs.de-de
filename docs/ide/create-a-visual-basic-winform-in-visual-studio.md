---
title: Erstellen einer Windows Forms-App mit Visual Basic
description: Erfahren Sie, wie Sie schrittweise eine Windows Forms-App in Visual Studio mit Visual Basic erstellen.
ms.date: 03/23/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 4619a56bfe052a1fb191af8edfd1cef8b376617b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976842"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Erstellen einer Windows Forms-App in Visual Studio mit Visual Basic

Mithilfe dieser kurzen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio können Sie eine einfache Visual Basic-Anwendung erstellen, die über eine Windows-basierte Benutzeroberfläche verfügt.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) kostenlos herunterladen.

> [!NOTE]
> Einige der Screenshots in diesem Tutorial verwenden das dunkle Design. Wenn Sie ebenfalls das dunkle Design verwenden möchten, finden Sie auf der Seite [Personalisieren der Visual Studio-IDE und des Editors](../ide/quickstart-personalize-the-ide.md) entsprechende Anweisungen.

::: moniker-end

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen Sie zunächst ein Visual Basic-Anwendungsprojekt. Der Projekttyp enthält schon bevor Sie mit der Bearbeitung beginnen alle Vorlagendateien, die Sie benötigen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie dann auf **Windows-Desktop**. Klicken Sie im mittleren Bereich auf **Windows Forms-App (.NET Framework)**. Nennen Sie die Datei `HelloWorld`.

     Wenn Ihnen die Projektvorlage **Windows Forms-App (.NET Framework)** nicht angezeigt wird, schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie in der oberen Menüleiste auf **Extras** > **Tools und Features abrufen**. Der Visual Studio-Installer wird gestartet. Wählen Sie beispielsweise die Workload **.NET-Desktopentwicklung** aus, und klicken Sie anschließend auf **Ändern**.

     ![Die Workload „.NET Core“ im Visual Studio-Installer](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Fenster „Neues Projekt erstellen“ anzeigen](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld den Begriff *Windows Forms* ein. Wählen Sie anschließend in der Liste der Sprachen **Visual Basic** und dann aus der Liste der Plattformen **Windows** aus. 

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie die Vorlage **Windows Forms-App (.NET Framework)** und dann **Weiter** aus.

   ![Screenshot: Auswählen der Visual Basic-Vorlage für die Windows Forms-App (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Wenn Sie die **Windows Forms-App (.NET Framework)** nicht sehen, können Sie sie aus dem Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus.
   >
   > ![Link „Weitere Tools und Features installieren“ aus der Meldung „Sie finden nicht, wonach Sie suchen“ im Fenster „Neues Projekt erstellen“](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Wählen Sie anschließend im Visual Studio-Installer die Workload **.NET Desktopentwicklung** aus.
   > 
   > ![Die Workload „.NET Core“ im Visual Studio-Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Wählen Sie anschließend die Schaltfläche **Ändern** im Visual Studio-Installer aus. Möglicherweise werden Sie aufgefordert, Ihre Arbeit zu speichern; wenn dies der Fall ist, führen Sie das aus. Wählen Sie als Nächstes **Weiter** aus, um die Workload zu installieren. Kehren Sie dann zu Schritt 2 in dieser Vorgehensweise "[Projekt erstellen](#create-a-project)" zurück.

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** *HalloWelt* ein. Wählen Sie anschließend **Erstellen** aus.

   ![Benennen Sie Ihr Projekt im Fenster „Neues Projekt konfigurieren“ „HalloWelt“](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio öffnet Ihr neues Projekt.

::: moniker-end

## <a name="create-the-application"></a>Erstellen der Anwendung

Sobald Sie eine Visual Basic-Projektvorlage ausgewählt und die Datei benannt haben, öffnet Visual Studio ein Formular für Sie. Ein Formular ist eine Windows-Benutzeroberfläche. Es soll eine „Hallo Welt“-Anwendung erstellt werden, indem dem Formular Steuerelemente hinzugefügt werden. Anschließend soll die Anwendung ausgeführt werden.

### <a name="add-a-button-to-the-form"></a>Hinzufügen einer Schaltfläche zum Formular

1. Klicken Sie auf **Toolbox**, um das „Toolbox ausfliegen“-Fenster zu öffnen.

     ![Klicken Sie auf „Toolbox“, um das Toolbox-Fenster zu öffnen.](../ide/media/vb-toolbox-toolwindow.png)

     (Wenn Ihnen die Flyoutoption **Toolbox** nicht angezeigt wird, können Sie sie öffnen, indem Sie **STRG**+**ALT**+**X** drücken.)

2. Klicken Sie auf das **Stecknadelsymbol**, um das **Toolbox-Fenster** anzudocken.

     ![Klicken Sie auf das Stecknadelsymbol, um das Toolbox-Fenster an die IDE anzuheften.](../ide/media/vb-pin-the-toolbox-window.png)

3. Klicken Sie auf das **Schaltflächen-Steuerelement**, und bewegen Sie dieses dann zum Formular.

     ![Hinzufügen einer Schaltfläche zum Formular](../ide/media/vb-add-a-button-to-form1.png)

4. Geben Sie im Fenster **Eigenschaften** im Abschnitt **Darstellung** (oder im Abschnitt **Schriftarten**) `Click this` ein, und drücken Sie dann die **EINGABETASTE**.

     ![Hinzufügen von Text zur Schaltfläche auf dem Formular](../ide/media/vb-button-control-text.png)

     (Wenn Ihnen das **Eigenschaftenfenster** nicht angezeigt wird, können Sie es über die Menüleiste öffnen. Klicken Sie dafür auf **Ansicht** > **Eigenschaftenfenster**. Oder drücken Sie **F4**.)

5. Ändern Sie im Fenster **Eigenschaften** im Abschnitt **Entwurf** den Namen von **Button1** in `btnClickThis`, und drücken Sie dann die **EINGABETASTE**.

     ![Hinzufügen einer Funktion zur Schaltfläche auf dem Formular](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Hinzufügen einer Bezeichnung zum Formular

Da nun ein Schaltflächen-Steuerelement hinzugefügt wurde, kann jetzt auch ein Bezeichnungs-Steuerelement hinzugefügt werden, an das Text gesendet werden kann, um eine Aktion zu erstellen.

1. Wählen Sie im **Toolbox**-Fenster das Steuerelement **Bezeichnung** aus, und ziehen Sie es dann unter die Schaltfläche **Click this** („Hier klicken“).

2. Ändern Sie im Fenster **Eigenschaften** im Abschnitt **Entwurf** den Namen von **Label1** in `lblHelloWorld`, und drücken Sie dann die **EINGABETASTE**.

### <a name="add-code-to-the-form"></a>Hinzufügen von Code zum Formular

1. Doppelklicken Sie im Fenster **Form1.vb [Entwurf]** auf die Schaltfläche **Click this** („Hier klicken“), um das Fenster **Form1.vb** zu öffnen.

      (Stattdessen können Sie auch **Form1.vb** im **Projektmappen-Explorer** erweitern und dann auf **Form1** klicken.)

2. Geben Sie im Fenster **Form1.vb** zwischen der Zeile **Private Sub** und der Zeile **End Sub** den folgenden Code ein (oder zwischen der Zeile **Public Class Form1** und der Zeile **End Class**).

     ![Hinzufügen von Code zum Formular](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Klicken Sie auf die Schaltfläche **Start**, um die Anwendung auszuführen.

     ![Klicken Sie auf „Start“, um die App auszuführen und zu debuggen.](../ide/media/vb-click-start-hello-world.png)

   Daraufhin werden einige Vorgänge gleichzeitig ausgeführt. In der Visual Studio-IDE öffnen sich das Fenster **Diagnosetools** und ein **Ausgabefenster**. Außerhalb der IDE wird das **Form1**-Dialogfeld angezeigt. Darin ist die Schaltfläche **Click this** („Hier klicken“) und Text mit dem Inhalt **Label1** enthalten.

2. Klicken Sie auf die Schaltfläche **Click this** („Hier klicken“) im Dialogfeld **Form1**. Beachten Sie, dass der Text **Label1** sich in **Hallo Welt!** ändert.

    ![Ein „Form1“-Dialogfeld, das den Text „Label1“ beinhaltet. ](../ide/media/vb-form1-dialog-hello-world.png)

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über Visual Basic und die Visual Studio-IDE gelernt haben. Wenn Sie mehr über diese Themen erfahren möchten, können Sie gerne mit einem Tutorial fortfahren, das Sie im Inhaltsverzeichnis im Abschnitt **Tutorials** finden.

## <a name="see-also"></a>Siehe auch

* [Schnellstart: Erstellen einer Konsolenanwendung in Visual Studio mit Visual Basic](quickstart-visual-basic-console.md)
* [Erfahren Sie mehr über Visual Basic IntelliSense](visual-basic-specific-intellisense.md)
