---
title: Hinzufügen eines Menücontrollers zu einer Symbolleiste | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740330"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Hinzufügen eines Menücontrollers zu einer Symbolleiste
Diese exemplarische Vorgehensweise basiert auf der exemplarischen Vorgehensweise hinzufügen zu [einer Exemplarleiste des Werkzeugfensters](../extensibility/adding-a-toolbar-to-a-tool-window.md) und zeigt, wie Sie der Symbolleiste des Werkzeugfensters einen Menücontroller hinzufügen. Die hier gezeigten Schritte können auch auf die Symbolleiste angewendet werden, die in der exemplarischen Vorgehensweise ["Symbolleiste hinzufügen"](../extensibility/adding-a-toolbar.md) erstellt wird.

Ein Menücontroller ist ein geteiltes Steuerelement. Auf der linken Seite des Menücontrollers wird der zuletzt verwendete Befehl angezeigt, den Sie ausführen können, indem Sie darauf klicken. Die rechte Seite des Menücontrollers ist ein Pfeil, der beim Klicken eine Liste zusätzlicher Befehle öffnet. Wenn Sie auf einen Befehl in der Liste klicken, wird der Befehl ausgeführt, und er ersetzt den Befehl auf der linken Seite des Menücontrollers. Auf diese Weise arbeitet der Menü-Controller wie eine Befehlsschaltfläche, die immer den zuletzt verwendeten Befehl aus einer Liste anzeigt.

Menücontroller können in Menüs angezeigt werden, werden aber am häufigsten auf Symbolleisten verwendet.

## <a name="prerequisites"></a>Voraussetzungen
Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Erstellen eines Menücontrollers

1. Befolgen Sie die unter [Hinzufügen einer Symbolleiste zu einem Werkzeugfenster](../extensibility/adding-a-toolbar-to-a-tool-window.md) beschriebenen Verfahren, um ein Werkzeugfenster mit einer Symbolleiste zu erstellen.

2. Gehen Sie in *TWTestCommandPackage.vsct*zum Abschnitt Symbole. Dein Menücontroller, Menücontrollergruppe und drei Menüelemente deklarieren im GuidSymbol-Element **guidTWTestPackagePackageCmdSet.**

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Definieren Sie im Abschnitt Menüs nach dem letzten Menüeintrag den Menücontroller als Menü.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    Die `TextChanges` `TextIsAnchorCommand` und Flags müssen enthalten sein, damit der Menücontroller den zuletzt ausgewählten Befehl wiedergibt.

4. Fügen Sie im Abschnitt Gruppen nach dem letzten Gruppeneintrag die Menücontrollergruppe hinzu.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Wenn Sie den Menücontroller als übergeordneten Befehl festlegen, werden alle in dieser Gruppe platzierten Befehle im Menücontroller angezeigt. Das `priority` Attribut wird weggelassen, wodurch es auf den Standardwert 0 festgelegt wird, da es die einzige Gruppe auf dem Menücontroller ist.

5. Fügen Sie im Abschnitt Schaltflächen nach dem letzten Schaltflächeneintrag ein Schaltflächenelement für jedes Menüelement hinzu.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. An dieser Stelle können Sie sich den Menücontroller ansehen. Erstellen Sie das Projekt, und starten Sie das Debugging. Sie sollten die experimentelle Instanz sehen.

   1. Öffnen Sie im Menü **Ansicht / Andere Windows** Test **ToolWindow**.

   2. Der Menücontroller wird auf der Symbolleiste im Werkzeugfenster angezeigt.

   3. Klicken Sie auf den Pfeil auf der rechten Seite des Menücontrollers, um die drei möglichen Befehle anzuzeigen.

      Beachten Sie, dass sich beim Klicken auf einen Befehl der Titel des Menücontrollers ändert, um diesen Befehl anzuzeigen. Im nächsten Abschnitt fügen wir den Code hinzu, um diese Befehle zu aktivieren.

## <a name="implement-the-menu-controller-commands"></a>Implementieren der Menücontrollerbefehle

1. Fügen Sie in *TWTestCommandPackageGuids.cs*Befehls-IDs für Ihre drei Menüelemente nach den vorhandenen Befehls-IDs hinzu.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. Fügen Sie in *TWTestCommand.cs*den folgenden `TWTestCommand` Code oben in der Klasse hinzu.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. Fügen Sie im TWTestCommand-Konstruktor nach `AddCommand` dem letzten Aufruf der Methode Code hinzu, um die Ereignisse für jeden Befehl über dieselben Handler weiterzuleiten.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Fügen Sie der **TWTestCommand-Klasse** einen Ereignishandler hinzu, um den ausgewählten Befehl als aktiviert zu markieren.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Fügen Sie einen Ereignishandler hinzu, der eine MessageBox anzeigt, wenn der Benutzer einen Befehl auf dem Menücontroller auswählt:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Testen des Menücontrollers

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Sie sollten die experimentelle Instanz sehen.

2. Öffnen Sie das **Test ToolWindow** im Menü **Ansicht / Andere Windows.**

    Der Menücontroller wird in der Symbolleiste im Werkzeugfenster angezeigt und zeigt **MC-Element 1**an.

3. Klicken Sie auf die Menü-Controller-Schaltfläche links neben dem Pfeil.

    Sie sollten drei Elemente sehen, von denen das erste ausgewählt ist und ein Hervorhebungsfeld um sein Symbol herum hat. Klicken Sie auf **MC-Element 3**.

    Es wird ein Dialogfeld mit der Meldung **Angezeigt angezeigt,** den Sie menü controller Item 3 ausgewählt haben. Beachten Sie, dass die Meldung dem Text auf der Menücontrollerschaltfläche entspricht. Die Menü-Controller-Schaltfläche zeigt nun **MC Item 3**an.

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen einer Symbolleiste zu einem Werkzeugfenster](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)
