---
title: Hinzufügen eines Menücontrollers zu einer Symbolleiste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13dec4b907b52e35b5b2377aafa511e50dc5cc48
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771535"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Hinzufügen eines Menücontrollers zu einer Symbolleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise baut auf den [ein Toolfenster eine Symbolleiste hinzugefügt](../extensibility/adding-a-toolbar-to-a-tool-window.md) Exemplarische Vorgehensweise und zeigt, wie die Toolfenster-Symbolleiste ein Menücontroller hinzugefügt. Die hier gezeigten Schritte auch können angewendet werden auf der Symbolleiste, die in erstellt haben, wird die [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md) Exemplarische Vorgehensweise.  
  
 Ein Menücontroller ist ein Split-Steuerelement. Die linke Seite des menücontrollers im zeigt des zuletzt verwendeten Befehls ein, und sie kann ausgeführt werden, indem Sie darauf klicken. Rechts neben dem Menücontroller wird als Pfeil dargestellt, die durch Klicken auf eine Liste mit zusätzlichen Befehlen geöffnet. Wenn Sie einen Befehl in der Liste der Befehl ausgeführt wird, klicken Sie auf, und er ersetzt den Befehl auf der linken Seite des menücontrollers im. Wird auf diese Weise die Menücontroller, wie eine Befehlsschaltfläche, die immer die zuletzt verwendeten Befehl in einer Liste anzeigt.  
  
 Menücontroller können in Menüs angezeigt werden, aber sie werden meist verwendet, auf der Symbolleiste.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Erstellen ein Menücontroller  
  
#### <a name="to-create-a-menu-controller"></a>Erstellen Sie ein Menücontroller  
  
1. Führen Sie die Schritte [ein Toolfenster eine Symbolleiste hinzugefügt](../extensibility/adding-a-toolbar-to-a-tool-window.md) ein Toolfenster erstellen, die eine Symbolleiste hat.  
  
2. Öffnen Sie in TWTestCommandPackage.vsct den Abschnitt "Symbols". In der GuidSymbol-Element, das mit dem Namen **GuidTWTestCommandPackageCmdSet**, deklarieren Sie Ihr Menücontroller, Controller Menügruppe und drei Menüelemente.  
  
   ```xml  
   <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
   ```  
  
3. Definieren Sie im Abschnitt Menüs hinter dem letzten Menüeintrag im, die Menücontroller als Menü aus.  
  
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
  
    Die `TextChanges` und `TextIsAnchorCommand` Flags müssen eingeschlossen werden, um den Menücontroller mit dem letzten ausgewählten Befehl entsprechend zu aktivieren.  
  
4. Fügen Sie in den Gruppen, das hinter dem letzten Gruppeneintrag im Abschnitt verwenden zu können, die Controller-Menügruppe.  
  
   ```xml  
   <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
   </Group>  
   ```  
  
    Wenn Sie den Menücontroller als übergeordnetes Element festlegen, werden alle Befehle, die in dieser Gruppe platziert in der Menücontroller im angezeigt. Die `priority` Attribut weggelassen wird, wodurch es auf den Standardwert 0 (null) festgelegt, da es die einzige Gruppe für den Menücontroller handelt.  
  
5. Fügen Sie im Abschnitt Schaltflächen hinter dem letzten Eintrag für die Schaltfläche für die einzelnen Elemente im Menü ein Button-Element hinzu.  
  
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
  
6. An diesem Punkt können Sie die Menücontroller ansehen. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden.  
  
   1. Auf der **anzeigen / Other Windows** öffnen **Test ToolWindow**.  
  
   2. Der Menücontroller wird auf der Symbolleiste im Toolfenster angezeigt.  
  
   3. Klicken Sie auf den Pfeil auf der rechten Seite des menücontrollers im auf die drei möglichen Befehle finden Sie unter.  
  
      Beachten Sie, dass wenn Sie einen Befehl klicken, wird der Titel des menücontrollers im ändert, um diesen Befehl anzuzeigen. Im nächsten Abschnitt fügen wir den Code, um diese Befehle aktivieren hinzu.  
  
## <a name="implementing-the-menu-controller-commands"></a>Implementieren die Controller-Befehle im Menü  
  
1.  Fügen Sie in TWTestCommandPackageGuids.cs Befehls-IDs für Ihre drei Menüelemente nach den vorhandenen Befehls-IDs ein.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  Fügen Sie in TWTestCommand.cs den folgenden Code am Anfang der TWTestCommand-Klasse.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  Im Konstruktor TWTestCommand nach dem letzten Aufruf von der `AddCommand` -Methode Code hinzufügen, um die Ereignisse für jeden Befehl über die gleichen Handler weitergeleitet.  
  
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
  
4.  Fügen Sie einen Ereignishandler, der TWTestCommand-Klasse, um den ausgewählten Befehl als aktivierten zu markieren.  
  
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
  
5.  Fügen Sie einen Ereignishandler, der eine MessageBox anzeigt, wenn der Benutzer einen Befehl auf dem Menücontroller im auswählt:  
  
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
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden.  
  
2.  Öffnen der **Test ToolWindow** auf die **anzeigen / Other Windows** Menü.  
  
     Der Menücontroller im auf der Symbolleiste im Toolfenster angezeigt wird, und zeigt **MC Element 1**.  
  
3.  Klicken Sie auf die Menüschaltfläche Controller, auf der linken Seite des Pfeils.  
  
     Drei Elemente enthält, sollte das erste Argument ausgewählt ist, und verfügt über ein Highlight-Feld, um das entsprechende Symbol angezeigt werden. Klicken Sie auf **MC Element 3**.  
  
     Ein Dialogfeld angezeigt wird, mit der Meldung **Menücontroller Element 3 ausgewählten**. Beachten Sie, dass die Meldung und dem Text in die Controller-Menüschaltfläche entspricht. Die Controller-Menüschaltfläche zeigt nun **MC Element 3**.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen einer Symbolleiste zu einem Toolfenster](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)

