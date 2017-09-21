---
title: "Hinzuf&#252;gen eines Controllers im Men&#252; auf einer Symbolleiste | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbolleisten [Visual Studio], Hinzufügen von Controllern im Menü"
  - "Menüs, Symbolleisten im Menücontroller hinzufügen"
  - "Menücontroller hinzufügen zu Symbolleisten"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# Hinzuf&#252;gen eines Controllers im Men&#252; auf einer Symbolleiste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise baut auf den [Ein Toolfenster hinzugefügt eine Symbolleiste](../extensibility/adding-a-toolbar-to-a-tool-window.md) Exemplarische Vorgehensweise und veranschaulicht das Hinzufügen ein Controllers im Menü auf der Symbolleiste des Toolfensters. Die hier gezeigten Schritte auch können angewendet werden auf die Symbolleiste, die in erstellt haben, wird die [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md) Exemplarische Vorgehensweise.  
  
 Ein Menü\-Controller ist ein Split\-Steuerelement. Zeigt den zuletzt verwendeten Befehl an der linken Seite des Controllers im Menü aus, und klicken Sie auf ausgeführt werden kann. Rechts neben den Menü\-Controller wird als Pfeil dargestellt, die durch Klicken auf eine Liste mit zusätzlichen Befehlen geöffnet. Wenn Sie einen Befehl in der Liste der Befehl ausgeführt wird, klicken Sie auf, und den Befehl auf der linken Seite des Controllers im Menü ersetzt. Auf diese Weise arbeitet der Controller im Menü wie eine Befehlsschaltfläche, die immer die zuletzt verwendeten Befehl in einer Liste anzeigt.  
  
 Menücontroller können in Menüs angezeigt werden, aber am häufigsten auf Symbolleisten verwendet werden.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines Controllers im Menü  
  
#### Zum Erstellen eines Controllers im Menü  
  
1.  Führen Sie die beschriebenen Schritte [Ein Toolfenster hinzugefügt eine Symbolleiste](../extensibility/adding-a-toolbar-to-a-tool-window.md) ein Toolfenster erstellen, die eine Symbolleiste enthält.  
  
2.  Finden Sie in TWTestCommandPackage.vsct im Abschnitt Symbole. Im Element GuidSymbol **GuidTWTestCommandPackageCmdSet**, der Menü\-Controller, Controller Menügruppe und drei Menüelemente deklariert.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  Klicken Sie im Abschnitt Menüs nach dem der letzte Menüeintrag im definieren Sie den Menü\-Controller als Menü.  
  
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
  
     Die `TextChanges` und `TextIsAnchorCommand` Flags So aktivieren Sie den Controller im Menü entsprechend den zuletzt ausgewählten Befehl eingeschlossen werden müssen.  
  
4.  Fügen Sie in den Gruppen hinter dem letzten Eintrag für die Gruppe im Abschnitt verwenden zu können, die Gruppe der Menü\-Controller.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Alle Befehle, die in dieser Gruppe platziert werden durch Festlegen des Menü\-Controllers als übergeordnetes Element, im Controller im Menü angezeigt. Die `priority` Attribut ausgelassen wird, die wird auf den Standardwert 0, da es die einzige Gruppe auf dem Menü Controller sein wird.  
  
5.  Fügen Sie im Abschnitt Schaltflächen hinter dem letzten Eintrag für die Schaltfläche ein Button\-Element für jedes der Menüelemente im aus.  
  
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
  
6.  An diesem Punkt können Sie den Controller im Menü anzeigen. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
    1.  Auf der **Anzeigen \/ andere Fenster** öffnen Sie im Menü **Test im**.  
  
    2.  Der Menü\-Controller wird auf der Symbolleiste im Toolfenster angezeigt.  
  
    3.  Klicken Sie auf den Pfeil auf der rechten Seite des Controllers im Menü auf die drei möglichen Befehle finden Sie unter.  
  
     Beachten Sie, dass wenn Sie einen Befehl klicken, wird der Titel des Controllers im Menü geändert, um diesen Befehl anzuzeigen. In im nächsten Abschnitt fügen wir den Code, um diese Befehle zu aktivieren.  
  
## Implementieren die Controller\-Menübefehle  
  
1.  Fügen Sie in TWTestCommandPackageGuids.cs Befehls\-IDs für die drei Menüelemente nach den vorhandenen Befehls\-IDs.  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  Fügen Sie in TWTestCommand.cs den folgenden Code am Anfang der TWTestCommand\-Klasse.  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  In den TWTestCommand\-Konstruktor nach dem letzten Aufruf der `AddCommand` \-Methode Code hinzufügen, um die Ereignisse für jeden Befehl über die gleichen Handler weitergeleitet.  
  
    ```c#  
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
  
4.  Fügen Sie einen Ereignishandler, um die TWTestCommand\-Klasse, um den ausgewählten Befehl als überprüft markieren.  
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Fügen Sie einen Ereignishandler, der eine MessageBox anzeigt, bei der Auswahl eines Befehls im Menü\-Controller:  
  
    ```c#  
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
  
## Testen den Controller im Menü  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
2.  Öffnen Sie die **Test im** auf der **Anzeigen \/ Weitere Fenster** Menü.  
  
     Der Controller im Menü auf der Symbolleiste im Toolfenster angezeigt und zeigt **MC Element 1**.  
  
3.  Klicken Sie auf die Schaltfläche auf der linken Seite des Pfeils Controller.  
  
     Drei Elemente enthält, sollte das erste Argument ausgewählt ist und verfügt über ein Highlight\-Feld, um dessen Symbol angezeigt werden. Klicken Sie auf **MC Element 3**.  
  
     Ein Dialogfeld mit der Meldung **ausgewählten Menü Controller Element 3**. Beachten Sie, dass die Nachricht den Text auf die Schaltfläche Controller entspricht. Die Controller\-Schaltfläche zeigt nun **MC Element 3**.  
  
## Siehe auch  
 [Ein Toolfenster hinzugefügt eine Symbolleiste](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)