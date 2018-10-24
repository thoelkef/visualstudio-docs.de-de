---
title: 'Schnellstart: Erstellen Ihrer ersten Anwendung für die universelle Windows-Plattform in Visual Studio mit XAML und C# | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology:
- vs-acquisition
ms.topic: quickstart
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a203d471d5947df9919ed8c9afe7d1c2d41296f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908907"
---
# <a name="quickstart-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Schnellstart: Erstellen Ihrer ersten Anwendung für die universelle Windows-Plattform in Visual Studio mit XAML und C&#35;

Mithilfe dieser Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio, die fünf bis zehn Minuten Ihrer Zeit in Anspruch nehmen wird, erstellen Sie eine „Hallo Welt“-App, die auf jedem beliebigen Windows 10-Gerät ausgeführt werden kann. Zu diesem Zweck verwenden Sie eine UWP-Projektvorlage (Universelle Windows-Plattform), XAML (Extensible Application Markup Language) und die C#-Programmiersprache.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen Sie zuerst ein UWP-Projekt (Universelle Windows-Plattform). Der Projekttyp enthält alle nötigen Vorlagendateien, schon bevor Sie mit der Bearbeitung beginnen.

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

3. Klappen Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Visual C#** auf, und wählen Sie **Universelles Windows** aus. Wählen Sie im mittleren Bereich **Leere App (universelles Windows)** aus. Benennen Sie das Projekt mit *HalloWelt*, und wählen Sie **OK**.

   ![Die Projektvorlage für universelles Windows im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](../ide/media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Falls Sie die Projektvorlage **Leere App (universelles Windows)** nicht finden, klicken Sie auf der linken Seite des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**.<br><br>![Klicken Sie auf den Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“.](../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Entwicklung für die universelle Windows-Plattform** aus, und klicken Sie dann auf **Ändern**.<br><br>![Workload für die Entwicklung für die universelle Windows-Plattform im Visual Studio-Installer](../ide/media/uwp-dev-workload.png)

4. Wenn das Dialogfeld **Neues UWP-Projekt (Universelle Windows-Plattform)** angezeigt wird, wählen Sie **OK**.

   ![Übernehmen Sie die Standardeinstellungen für Zielversion und Mindestversion im Dialogfeld „Neues UWP-Projekt (Universelle Windows-Plattform)“.](../ide/media/new-uwp-project-target-minver-dialog.png)

   > [!NOTE]
   > Wenn Sie Visual Studio erstmals zum Erstellen einer UWP-App verwenden, wird möglicherweise ein Dialogfeld **Einstellungen** angezeigt. Wählen Sie **Entwicklermodus**, und wählen Sie dann **Ja**.<br><br>
   ![Aktivieren Sie den Entwicklermodus im Dialogfeld mit UWP-Einstellungen.](../ide/media/enable-developer-mode.png)<br><br>Visual Studio installiert für Sie ein zusätzliches Entwicklermoduspaket. Wenn die Paketinstallation abgeschlossen ist, schließen Sie das Dialogfeld **Einstellungen**.

## <a name="create-the-application"></a>Erstellen der Anwendung

Beginnen wir jetzt mit der Entwicklung. Sie fügen ein Schaltflächensteuerelement hinzu, fügen der Schaltfläche eine Aktion hinzu und starten dann die App „Hallo Welt“, um sie sich anzusehen.

### <a name="add-a-button-to-the-design-canvas"></a>Hinzufügen einer Schaltfläche zur Entwurfs-Canvas

1. Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei *MainPage.xaml*, um eine geteilte Ansicht zu öffnen.

   ![Öffnen Sie im Projektmappen-Explorer die Datei „MainPage.xaml“. ](../ide/media/uwp-solution-explorer-MainPage-xaml.png)

   Sie sehen zwei Bereiche: den **XAML-Designer** mit einer Entwurfs-Canvas und den **XAML-Editor** zum Hinzufügen oder Ändern von Code.

   ![Der XAML-Designer-Bereich im XAML-Editor](../ide/media/uwp-xaml-editor.png)

2. Klicken Sie auf **Toolbox**, um das Toolbox-Flyoutfenster zu öffnen.

   ![Klicken Sie auf „Toolbox“, um das Toolbox-Flyoutfenster zu öffnen.](../ide/media/uwp-toolbox.png)

   (Wenn Ihnen die Option **Toolbox** nicht angezeigt wird, können Sie sie über die Menüleiste öffnen. Hierzu wählen Sie **Ansicht** > **Symbolleiste**. Drücken Sie alternativ auf **STRG**+**ALT**+**X**.)

3. Klicken Sie auf das **Stecknadelsymbol**, um das Toolbox-Fenster anzudocken.

   ![Klicken Sie auf das Stecknadelsymbol, um das Toolbox-Fenster anzudocken.](../ide/media/uwp-toolbox-autohide.png)

4. Klicken Sie auf das Steuerelement **Schaltfläche**, und ziehen Sie es auf die Entwurfs-Canvas.

   ![Klicken Sie auf das Steuerelement „Schaltfläche“, und ziehen Sie es auf die Entwurfs-Canvas.](../ide/media/uwp-toolbox-add-button-control.png)

   Wenn Sie den Code im **XAML-Editor** betrachten, sehen Sie, dass die Schaltfläche auch dort hinzugefügt wurde:

   ![Klicken Sie auf das Steuerelement „Schaltfläche“, und ziehen Sie es auf die Entwurfs-Canvas.](../ide/media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Hinzufügen einer Bezeichnung zur Schaltfläche

1. Ändern Sie im **XAML-Editor** den Wert für den Schaltflächeninhalt von „Schaltfläche“ in „Hallo Welt!“

   ![Ändern Sie den Wert für den Schaltflächeninhalt in „Hallo Welt“.](../ide/media/uwp-change-button-text-in-xaml-code-window.png)

2. Beachten Sie, dass die Schaltfläche auch im **XAML-Designer** geändert wird.

   ![Die Schaltfläche ändert sich auf der Entwurfs-Canvas in „Hallo Welt“.](../ide/media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Hinzufügen eines Ereignishandlers

Ein „Ereignishandler“ klingt kompliziert, ist aber nur ein anderer Name für Code, der aufgerufen wird, wenn ein Ereignis eintritt. In diesem Fall fügt er der Schaltfläche „Hallo Welt!“ eine Aktion Schaltfläche.

1. Doppelklicken Sie auf der Entwurfs-Canvas auf das Steuerelement „Schaltfläche“.

2. Bearbeiten Sie den Ereignishandlercode in *MainPage.Xaml.cs*, der CodeBehind-Seite.

   An dieser Stelle wird es interessant. Der Standardereignishandler sieht folgendermaßen aus:

   ![Der Standardereignishandler für „Button_Click“ ](../ide/media/uwp-button-click-code.png)

   Wir ändern ihn folgendermaßen:

    ![Der neue asynchrone Ereignishandler für „Button_Click“ ](../ide/media/uwp-add-hello-world-async-code.png)

   Hier finden Sie den Code zum Kopieren und Einfügen:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

#### <a name="what-did-we-just-do"></a>Was haben wir gerade getan?

Der Code verwendet einige Windows-APIs, um eine Sprachsyntheseobjekt zu erstellen, und weist diesem dann Text für die Ausgabe zu. (Weitere Informationen zur Verwendung von `SpeechSynthesis` finden Sie unter <xref:System.Speech.Synthesis>.)

## <a name="run-the-application"></a>Ausführen der Anwendung

Jetzt können wir die UWP-App „Hallo Welt“ erstellen, bereitstellen und starten, um sie uns anzusehen. Gehen Sie folgendermaßen vor:

1. Wählen Sie **Lokaler Computer**, um die Anwendung zu starten.

   ![Klicken Sie auf lokaler Computer, um Ihre UWP-App zu starten und zu debuggen.](../ide/media/uwp-start-or-debug.png)

   (Alternativ können Sie in der Menüleiste **Debuggen** > **Debugging starten** wählen oder **F5** drücken, um Ihre App zu starten.)

2. Sehen Sie sich Ihre App an, die gleich nach der Anzeige eines Begrüßungsbildschirms angezeigt wird. Die App sollte ungefähr folgendermaßen aussehen:

   ![Eine UWP-App „Hallo Welt“](../ide/media/uwp-hello-world-app.png)

3. Klicken Sie auf die Schaltfläche **Hallo Welt**.

   Ihr Windows 10-Gerät sagt laut „Hallo Welt!“.

4. Klicken Sie in der Symbolleiste auf die Schaltfläche **Debuggen beenden**, um die App zu schließen. (Alternativ können Sie in der Menüleiste auf **Debuggen** > **Debuggen beenden** klicken oder **UMSCHALTTASTE**+**F5** drücken.)

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, Sie haben einige Grundlagen zu UWP und der Visual Studio-IDE erlernt. Fahren Sie für weitere Informationen mit dem folgenden Tutorial fort:

> [!div class="nextstepaction"]
> [Erstellen einer Benutzeroberfläche](/windows/uwp/design/basics/xaml-basics-ui)
