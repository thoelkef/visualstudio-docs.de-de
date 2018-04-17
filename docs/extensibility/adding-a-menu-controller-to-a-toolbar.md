---
title: Hinzufügen einer Symbolleiste ein Menücontroller | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63db98df400333216f5e753f8b6f82a61e785cd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Eine Symbolleiste hinzugefügt ein Menücontroller
Diese exemplarische Vorgehensweise basiert auf der [ein Toolfenster eine Symbolleiste hinzugefügt](../extensibility/adding-a-toolbar-to-a-tool-window.md) Exemplarische Vorgehensweise und gezeigt, wie die Symbolleiste des Toolfensters ein Menücontroller hinzugefügt. Die hier gezeigten Schritte auch können angewendet werden auf der Symbolleiste, die in erstellt haben, ist die [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md) Exemplarische Vorgehensweise.  
  
 Ein Menücontroller ist ein Split-Steuerelement. Der linken Seite des Controllers im Menü werden mit dem zuletzt verwendete Befehl und es kann ausgeführt werden, indem Sie darauf klicken. Rechts neben den Menücontroller wird als Pfeil dargestellt, die durch Klicken auf eine Liste mit zusätzlichen Befehlen geöffnet. Wenn Sie einen Befehl in der Liste der Befehl ausgeführt wird, klicken Sie auf, und den Befehl auf der linken Seite des Controllers Menü ersetzt. Auf diese Weise funktioniert die Menücontroller, wie eine Befehlsschaltfläche, die immer die zuletzt verwendeten Befehl aus einer Liste anzeigt.  
  
 Menüsteuerelemente können auf Menüs angezeigt werden, aber sie werden am häufigsten verwendet, auf der Symbolleiste.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Erstellen ein Menücontroller  
  
#### <a name="to-create-a-menu-controller"></a>So erstellen ein Menücontroller  
  
1.  Führen Sie die in beschriebenen Verfahren [ein Toolfenster eine Symbolleiste hinzugefügt](../extensibility/adding-a-toolbar-to-a-tool-window.md) ein Toolfenster erstellen, die eine Symbolleiste hat.  
  
2.  TWTestCommandPackage.vsct wechseln Sie zum Abschnitt Symbole. In der GuidSymbol-Element mit dem Namen **GuidTWTestCommandPackageCmdSet**, Ihre Menücontroller, Menü-Domänencontrollergruppe und drei Menüelemente deklariert.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  Definieren Sie im Abschnitt Menüs nach der letzten Menüeintrag der Menücontroller als Menü.  
  
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
  
     Die `TextChanges` und `TextIsAnchorCommand` Flags So aktivieren Sie die Menücontroller entsprechend den letzten ausgewählten Befehl eingeschlossen werden müssen.  
  
4.  Fügen Sie in den Gruppen nach der letzten Gruppe Eintrag im Abschnitt verwenden zu können, im Menü-Controller-Gruppe.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Alle Befehle, die in dieser Gruppe platziert werden durch Festlegen der Menücontroller als übergeordnetes Element, im Menücontroller im angezeigt. Die `priority` Attribut weggelassen wird, wodurch er auf den Standardwert 0, da es die einzige Gruppe auf dem Menücontroller im werden.  
  
5.  Fügen Sie Schaltflächen im Abschnitt hinter dem letzten Eintrag für die Schaltfläche ein Button-Element für jedes der Menüelemente im hinzu.  
  
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
  
6.  An diesem Punkt können Sie die Menücontroller betrachten. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
    1.  Auf der **Ansicht / Weitere Fenster** öffnen Sie im Menü **Test (Toolfenster)**.  
  
    2.  Der Menücontroller im wird auf der Symbolleiste im Toolfenster angezeigt.  
  
    3.  Klicken Sie auf den Pfeil auf der rechten Seite des Controllers im Menü auf die drei möglichen Befehle finden Sie unter.  
  
     Beachten Sie, dass wenn Sie einen Befehl klicken, wird der Titel des Controllers im Menü zum Anzeigen dieser Befehls ändert. Im nächsten Abschnitt werden wir den Code, um diese Befehle aktivieren hinzufügen.  
  
## <a name="implementing-the-menu-controller-commands"></a>Implementieren die Menübefehle-Controller  
  
1.  Fügen Sie im TWTestCommandPackageGuids.cs Befehls-IDs für die drei Menüelemente nach den vorhandenen Befehls-IDs.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  Fügen Sie in TWTestCommand.cs den folgenden Code am Anfang der TWTestCommand-Klasse.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  Im Konstruktor TWTestCommand nach dem letzten Aufruf von der `AddCommand` -Methode Code hinzufügen, um die Ereignisse für jeden Befehl über die gleichen Handler weiterzuleiten.  
  
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
  
4.  Fügen Sie einen Ereignishandler, um die TWTestCommand-Klasse, um den ausgewählten Befehl als überprüft markiert.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Fügen Sie einen Ereignishandler, der eine MessageBox anzeigt, wenn der Benutzer einen Befehl auf dem Menücontroller im auswählt:  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
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
  
## <a name="testing-the-menu-controller"></a>Testen der Menücontroller  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
2.  Öffnen der **Test (Toolfenster)** auf die **Ansicht / Weitere Fenster** Menü.  
  
     Der Menücontroller im angezeigt wird, in der Symbolleiste auf das Toolfenster und zeigt **MC Element 1**.  
  
3.  Klicken Sie auf die Menüschaltfläche Controller auf der linken Seite des Pfeils.  
  
     Das erste ausgewählt ist, und verfügt über eine Markierungsfeld, um das Symbol sollte drei Elemente angezeigt werden. Klicken Sie auf **MC Element 3**.  
  
     Ein Dialogfeld wird angezeigt, mit der Meldung **Menücontroller Element 3 gewählte**. Beachten Sie, dass die Meldung für den Text auf die Menüschaltfläche Controller entspricht. Zeigt die Menüschaltfläche Controller jetzt **MC Element 3**.  
  
## <a name="see-also"></a>Siehe auch  
 [Ein Toolfenster hinzugefügt eine Symbolleiste](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)