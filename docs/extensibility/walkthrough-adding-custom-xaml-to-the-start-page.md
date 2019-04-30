---
title: 'Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML zur Startseite | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2ee368224eb4991a2f1f167d565bd2b07f85d4c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953074"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML zur Startseite

Diese exemplarische Vorgehensweise veranschaulicht eine benutzerdefinierte Startseite von Visual Studio zu erstellen, die enthält einen Webbrowser.

## <a name="add-custom-xaml"></a>Hinzufügen von benutzerdefinierten XAML

1. Erstellen Sie eine Startseite mithilfe der Anweisungen in [erstellen eine benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md).

2. In der *"MainWindow.xaml"* Datei, suchen die \<Raster > Abschnitt.

3. Hinzufügen einer \<TabControl > Element und ein \<TabItem > innerhalb der \< Raster > Element, wie im folgenden Beispiel dargestellt.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Fügen Sie eine zweite \<TabItem >, mit einem \<Schaltfläche >-Element, das ein neues Projekt wird geöffnet:

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>Testen Sie die benutzerdefinierte Startseite

1. Drücken Sie **F5**.

     Die experimentelle Instanz von Visual Studio wird geöffnet, mit die benutzerdefinierte Startseite installiert, aber nicht ausgewählt ist.

2. Öffnen Sie in der experimentellen Instanz von Visual Studio die **Extras/Optionen / Umgebung** Seite.

3. Wählen Sie **Start**. Auf der **Customize Start Page** Liste Ihrer *XAML* Datei, und klicken Sie auf **OK**.

4. Klicken Sie im Menü **Ansicht** auf **Startseite**.

5. Klicken Sie auf die **Bing** Registerkarte.

     Daraufhin sollte eine Bing-Webseite.

6. Klicken Sie auf die **MyButton** Registerkarte.

     Daraufhin sollte eine **"meinProjekt"** Schaltfläche daraufhin die **neues Projekt** Dialogfeld.

7. Schließen Sie die experimentelle Instanz.

Anwenden die benutzerdefinierten Startseite in **Tools** > **Optionen** > **Umgebung**Option **Start**. Auf der **Customize Start Page** Liste Ihrer *XAML* Datei, und klicken Sie auf **OK**.

## <a name="next-steps"></a>Nächste Schritte

Die Visual Studio-Startseite enthält jetzt eine Registerkarte, die eine Registerkarte des Webbrowsers und eine Registerkarte "MyButton" angezeigt. Sie können benutzerdefinierte Startseiten, mit denen andere Funktionen erstellen den *Code-Behind* Modell eine benutzerdefinierte DLL-Datei hinzufügen, siehe [Benutzersteuerelement hinzufügen, um die Startseite](../extensibility/adding-user-control-to-the-start-page.md). Sie können benutzerdefinierte Startseiten für andere Benutzer freigeben, veröffentlichen Sie die resultierende VSIX-Datei in die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website oder eine andere Website oder Netzwerk. Weitere Informationen finden Sie unter [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Siehe auch

- [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF-Container-Steuerelemente](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)