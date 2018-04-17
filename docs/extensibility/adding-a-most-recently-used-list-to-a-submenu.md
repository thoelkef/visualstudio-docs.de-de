---
title: Hinzufügen einer zuletzt verwendeten Liste aus, um ein Untermenü | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67eb08feff5d8edd1251c8fcff09d8f148b51b96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Liste aus, um ein Untermenü verwendet eine vor kurzem hinzufügen
Diese exemplarische Vorgehensweise basiert auf den Demos in [ein Menü ein Untermenü hinzugefügt](../extensibility/adding-a-submenu-to-a-menu.md), und zeigt, wie eine dynamische Liste ein Untermenü hinzugefügt. Die dynamische Liste bildet die Grundlage für die Erstellung einer Liste der zuletzt verwendeten (MRU).  
  
 Eine dynamische Menüliste wird durch einen Platzhalter in einem Menü gestartet. Jedes Mal, wenn Sie im Menü angezeigt wird, fordert der integrierten Entwicklungsumgebung (IDE) von Visual Studio das VSPackage für alle Befehle, die auf den Platzhalter angezeigt werden sollen. Eine dynamische Liste kann eine beliebige Stelle in einem Menü auftreten. Dynamische Listen werden jedoch in der Regel gespeichert und selbst angezeigt wird, Untermenüs oder auf die unten von Menüs. Verwenden Sie diese Entwurfsmuster, können Sie die dynamische Liste von Befehlen, die Erweiterung und Verkleinerung ohne Auswirkungen auf die Position der anderen Befehle im Menü aus. In dieser exemplarischen Vorgehensweise wird die dynamische MRU-Liste am unteren Rand einer vorhandenen Untermenü, das getrennt vom Rest der im Untermenü durch eine Linie angezeigt.  
  
 Technisch gesehen ist kann eine dynamische Liste auch zu einer Symbolleiste angewendet werden. Allerdings von wir daran, dass eine Symbolleiste unverändert bleiben soll, wenn der Benutzer bestimmte Schritte ändern, nimmt diese Verwendung abgeraten.  
  
 In dieser exemplarischen Vorgehensweise erstellt eine MRU-Liste von vier Elementen, die die Reihenfolge zu ändern, jedes Mal, dass eine von ihnen ausgewählt wird (das ausgewählte Element wird an den Anfang der Liste verschoben).  
  
 Weitere Informationen über Menüs und VSCT-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Erstellen eine Erweiterung  
  
-   Führen Sie die Verfahren in [ein Menü ein Untermenü hinzugefügt](../extensibility/adding-a-submenu-to-a-menu.md) So erstellen in den folgenden Verfahren das Untermenü die Option, die geändert werden.  
  
 Die Prozeduren in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Name des VSPackage `TopLevelMenu`, dies ist der Name, der verwendet wird [der Visual Studio-Menüleiste ein Menü hinzugefügt](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Erstellen einen dynamisches Element List-Befehl  
  
1.  Öffnen Sie TestCommandPackage.vsct.  
  
2.  In der `Symbols` im Abschnitt der `GuidSymbol` Knoten mit dem Namen GuidTestCommandPackageCmdSet, fügen Sie das Symbol für die `MRUListGroup` Gruppe und die `cmdidMRUList` Befehl wie folgt.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  In der `Groups` Abschnitt, der Gruppe "deklarierte" nach der vorhandenen Gruppeneinträge hinzufügen.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  In der `Buttons` Abschnitt, fügen Sie einen Knoten, um den neu deklarierten Befehl nach der vorhandenen Schaltfläche Einträge darstellen.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     Die `DynamicItemStart` -Flag ermöglicht, den Befehl aus, um dynamisch generiert werden soll.  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debuggen, um die Anzeige des neuen Befehls zu testen.  
  
     Auf der **TestMenu** Menü klicken Sie auf das neue Untermenü **Untermenü**, um den neuen Befehl anzuzeigen **MRU-Platzhalter**. Nachdem eine dynamische MRU-Liste der Befehle in der nächsten Prozedur implementiert ist, wird dieser Befehl Bezeichnung von dieser Liste jedes Mal ersetzt, die im Untermenü geöffnet wird.  
  
## <a name="filling-the-mru-list"></a>Füllen die MRU-Liste  
  
1.  Fügen Sie die folgenden Zeilen in TestCommandPackageGuids.cs, nachdem die vorhandenen Befehls-IDs in der `TestCommandPackageGuids` Klassendefinition.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  Fügen Sie TestCommand.cs folgende Anweisung verwenden.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Fügen Sie den folgenden Code im Konstruktor TestCommand nach dem letzten AddCommand-Aufruf. Die `InitMRUMenu` später definiert werden  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Fügen Sie den folgenden Code in der TestCommand-Klasse. Dieser Code initialisiert die Liste von Zeichenfolgen, die darstellen, die Elemente an die MRU-Liste angezeigt werden sollen.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  Nach der `InitializeMRUList` -Methode, Hinzufügen der `InitMRUMenu` Methode. Dadurch wird die Menübefehle für MRU-Liste initialisiert.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     Sie müssen ein Menü Command-Objekt für jedes mögliche Element in der Liste der zuletzt verwendeten Objekte erstellen. Ruft die IDE die `OnMRUQueryStatus` Methode für jedes Element in der Liste der zuletzt verwendeten bis keine Elemente mehr vorhanden sind. Die einzige Möglichkeit für die IDE zu wissen, dass es keine Elemente mehr sind werden in verwaltetem Code zuerst allen mögliche Elementen zu erstellen. Wenn Sie möchten, können Sie zusätzliche Elemente als nicht sichtbar ist, auf zuerst markieren, mit `mc.Visible = false;` nach der Menübefehl erstellt wird. Diese Elemente können dann sichtbar gemacht werden später mithilfe von `mc.Visible = true;` in die `OnMRUQueryStatus` Methode.  
  
6.  Nach der `InitMRUMenu` -Methode, fügen Sie die folgenden `OnMRUQueryStatus` Methode. Dies ist der Handler, der den Text für jede MRU-Element festlegt.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Nach der `OnMRUQueryStatus` -Methode, fügen Sie die folgenden `OnMRUExec` Methode. Dies ist der Handler für das Auswählen eines MRU-Elements. Diese Methode verschiebt das ausgewählte Element an den Anfang der Liste, und klicken Sie dann das ausgewählte Element in einem Meldungsfeld angezeigt.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>Testen der MRU-Liste  
  
#### <a name="to-test-the-mru-menu-list"></a>So testen Sie die Liste der zuletzt verwendeten-Menü  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debuggen  
  
2.  Auf der **TestMenu** Menü klicken Sie auf **aufrufen TestCommand**. Dies zeigt ein Meldungsfeld an, der angibt, dass der Befehl ausgewählt wurde.  
  
    > [!NOTE]
    >  Dieser Schritt ist erforderlich, erzwingen Sie das VSPackage, um das Laden und die MRU-Liste richtig angezeigt. Wenn Sie diesen Schritt überspringen, wird die MRU-Liste nicht angezeigt.  
  
3.  Auf der **Testmenü** Menü klicken Sie auf **Untermenü**. Eine Liste mit vier Elementen wird am Ende der im Untermenü unter eine Trennlinie angezeigt. Beim Klicken auf **Element 3**, ein Meldungsfeld angezeigt werden soll, und der Text "Selected Item 3" angezeigt. (Wenn die Liste der vier Elemente nicht angezeigt wird, stellen Sie sicher, dass Sie die Anweisungen in einem vorhergehenden Schritt ausgeführt haben.)  
  
4.  Öffnen Sie das Untermenü die Option erneut. Beachten Sie, dass **Element 3** ist jetzt am oberen Rand der Liste und die anderen Elemente Push ausgeführt wurde, eine Position nach unten. Klicken Sie auf **Element 3** erneut aus, und beachten Sie, dass weiterhin zeigt das Meldungsfeld "Selected Item 3", der angibt, dass der Text korrekt auf die neue Position zusammen mit der Bezeichnung Befehl verschoben wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamisches Hinzufügen von Menüelementen](../extensibility/dynamically-adding-menu-items.md)