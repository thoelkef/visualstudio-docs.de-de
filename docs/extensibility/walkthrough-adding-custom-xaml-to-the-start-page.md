---
title: 'Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697675"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine benutzerdefinierte Visual Studio-Startseite erstellen, die einen Webbrowser enthält.

## <a name="add-custom-xaml"></a>Hinzufügen von benutzerdefiniertem XAML

1. Erstellen Sie eine Startseite, indem Sie den Anweisungen unter [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md)folgen.

2. Suchen Sie in der Datei *MainWindow.xaml* den \<Abschnitt Grid>.

3. Fügen \<Sie ein TabControl->-Element und einen \<TabItem-> innerhalb des \< Grid->-Elements hinzu, wie im folgenden Beispiel gezeigt.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Fügen Sie \<ein zweites TabItem-> hinzu, mit einem \<Button->-Element, das ein neues Projekt öffnet:

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

## <a name="test-the-custom-start-page"></a>Testen der benutzerdefinierten Startseite

1. Drücken Sie **F5**.

     Die experimentelle Instanz von Visual Studio wird geöffnet, wobei die benutzerdefinierte Startseite installiert, aber nicht ausgewählt ist.

2. Öffnen Sie in der experimentellen Instanz von Visual Studio die Seite **Extras /Optionen / Umgebung.**

3. Wählen Sie **Start**. Wählen Sie in der Liste **Startseite anpassen** Ihre *.xaml-Datei* aus, und klicken Sie auf **OK**.

4. Klicken Sie im Menü **Ansicht** auf **Startseite**.

5. Klicken Sie auf die **Registerkarte Bing.**

     Es sollte eine Bing-Webseite angezeigt werden.

6. Klicken Sie auf die Registerkarte **MyButton.**

     Es sollte eine **MyProject-Schaltfläche** angezeigt werden, die das Dialogfeld **Neues Projekt** öffnet.

7. Schließen Sie die experimentelle Instanz.

Um die benutzerdefinierte Startseite anzuwenden, wählen Sie unter **Tools** > **Options** > **Environment**die Option **Start**aus. Wählen Sie in der Liste **Startseite anpassen** Ihre *.xaml-Datei* aus, und klicken Sie auf **OK**.

## <a name="next-steps"></a>Nächste Schritte

Die Startseite von Visual Studio enthält jetzt eine Registerkarte, auf der eine Webbrowser-Registerkarte und eine MyButton-Registerkarte angezeigt wird. Sie können benutzerdefinierte Startseiten mit anderen Funktionen erstellen, indem Sie das *CodeBehind-Modell* verwenden, um eine benutzerdefinierte DLL hinzuzufügen, wie unter [Hinzufügen der Benutzersteuerung zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)gezeigt. Sie können benutzerdefinierte Startseiten für andere Benutzer freigeben, indem Sie die resultierende .vSix-Datei auf der [Visual Studio Marketplace-Website](https://marketplace.visualstudio.com/) oder auf einer anderen Website oder Netzwerkfreigabe veröffentlichen. Weitere Informationen finden Sie unter [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Weitere Informationen

- [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF-Containersteuerelemente](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
