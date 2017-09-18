---
title: "Liste aus, um ein Untermen&#252; verwendet ein vor kurzem hinzuf&#252;gen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MRU-Listen"
  - "Menüs, Erstellen von MRU-Liste"
  - "zuletzt verwendet"
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 46
---
# Liste aus, um ein Untermen&#252; verwendet ein vor kurzem hinzuf&#252;gen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise baut auf den Demos in [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md), und zeigt, wie ein Untermenü eine dynamische Liste hinzugefügt. Die dynamische Liste bildet die Grundlage zum Erstellen einer Liste der zuletzt verwendet \(MRU\).  
  
 Eine dynamisches Menüliste beginnt mit einem Platzhalter in einem Menü. Jedes Mal, wenn Sie im Menü angezeigt wird, fordert der integrierten Entwicklungsumgebung \(IDE\) von Visual Studio das VSPackage alle Befehle, die auf den Platzhalter angezeigt werden soll. Eine dynamische Liste kann eine beliebige Stelle in einem Menü auftreten. Dynamische Listen werden jedoch in der Regel gespeichert und selbst angezeigt wird, Untermenüs oder auf die unten Menüs. Verwenden Sie diese Entwurfsmuster, können Sie die dynamische Liste der Befehle zum Vergrößern oder verkleinern, ohne die Position der anderen Befehle im Menü. In dieser exemplarischen Vorgehensweise wird die dynamische MRU\-Liste am unteren Rand einer vorhandenen Untermenü, das getrennt vom Rest der im Untermenü durch eine Linie angezeigt.  
  
 Technisch gesehen kann eine dynamische Liste auch zu einer Symbolleiste angewendet werden. Allerdings raten wir diese Verwendung, da eine Symbolleiste unverändert bleiben soll, wenn der Benutzer eine bestimmte Schritte ändern ausführt.  
  
 In dieser exemplarischen Vorgehensweise erstellt eine MRU\-Liste von vier Elemente, die ihre Reihenfolge zu ändern, jedes Mal, dass eine von ihnen ausgewählt ist \(das ausgewählte Element wechselt an den Anfang der Liste\).  
  
 Weitere Informationen zu Menüs und VSCT\-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Erstellen eine Erweiterung  
  
-   Gehen Sie wie unter [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md) Erstellen Sie in den folgenden Verfahren das Untermenü, das geändert wurde.  
  
 Die Verfahren in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Name des VSPackage `TopLevelMenu`, ist der verwendete Name ist [Der Visual Studio\-Menüleiste hinzufügen ein Menü](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## Erstellen eines dynamischen Elements Liste\-Befehls  
  
1.  Öffnen Sie TestCommandPackage.vsct.  
  
2.  In der `Symbols` im Abschnitt der `GuidSymbol` Knoten mit dem Namen GuidTestCommandPackageCmdSet, fügen Sie das Symbol für die `MRUListGroup` Gruppe und die `cmdidMRUList` Befehl wie folgt.  
  
    ```c#  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  In der `Groups` Abschnitt deklarierte Gruppe nach der vorhandenen Gruppeneinträge hinzufügen.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  In der `Buttons` enthält, fügen Sie einen Knoten, um den neu deklarierten Befehl ein, nach der vorhandenen Schaltfläche Einträge darstellen.  
  
    ```c#  
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
  
     Die `DynamicItemStart` Flag mit dem Befehl dynamisch generiert werden kann.  
  
5.  Erstellen Sie das Projekt, und starten Sie debugging, um die Anzeige von den neuen Befehl zu testen.  
  
     Auf der **TestMenu** Menü klicken Sie auf das neue Untermenü, **Untermenü**, um den neuen Befehl anzeigen **MRU\-Platzhalter**. Nachdem eine dynamische MRU\-Liste der Befehle in der nächsten Prozedur implementiert ist, wird dieser Befehl Beschriftung von dieser Liste jedes Mal ersetzt, die das Untermenü geöffnet wird.  
  
## Füllen die MRU\-Liste  
  
1.  Fügen Sie die folgenden Zeilen in TestCommandPackageGuids.cs, nachdem die vorhandenen Befehls\-IDs in der `TestCommandPackageGuids` Klassendefinition.  
  
    ```c#  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  TestCommand.cs fügen Sie folgende using\-Anweisung.  
  
    ```c#  
    using System.Collections;  
    ```  
  
3.  Fügen Sie den folgenden Code im Konstruktor TestCommand nach dem letzten AddCommand\-Aufruf. Die `InitMRUMenu` Weiter unten definiert wird  
  
    ```c#  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Fügen Sie den folgenden Code in der TestCommand\-Klasse. Dieser Code initialisiert die Liste von Zeichenfolgen, die darstellen, die Elemente auf der MRU\-Liste angezeigt werden.  
  
    ```c#  
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
  
5.  Nach der `InitializeMRUList` \-Methode hinzufügen die `InitMRUMenu` Methode. Dadurch wird die Menübefehle für MRU\-Liste initialisiert.  
  
    ```c#  
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
  
     Sie müssen ein Menü Command\-Objekt für jedes mögliche Element in der MRU\-Liste erstellen. Die IDE\-Aufrufe der `OnMRUQueryStatus` Methode für jedes Element in der MRU\-Liste, bis keine weiteren Elemente vorhanden sind. In verwaltetem Code ist die einzige Möglichkeit für die IDE zu wissen, dass keine Elemente mehr vorhanden sind, zunächst alle möglichen Elemente zu erstellen. Wenn Sie möchten, können Sie zusätzliche Elemente als nicht sichtbar ist, auf zuerst markieren, mit `mc.Visible = false;` nach der Erstellung des Menübefehls. Diese Elemente können dann sichtbar gemacht werden später mithilfe von `mc.Visible = true;` in die `OnMRUQueryStatus` Methode.  
  
6.  Nach der `InitMRUMenu` \-Methode, fügen Sie die folgenden `OnMRUQueryStatus` Methode. Dies ist der Handler, der den Text für jedes MRU\-Element festlegt.  
  
    ```c#  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Nach der `OnMRUQueryStatus` \-Methode, fügen Sie die folgenden `OnMRUExec` Methode. Dies ist der Handler für das Auswählen eines MRU\-Elements. Diese Methode verschiebt das ausgewählte Element an den Anfang der Liste und anschließend das ausgewählte Element in einem Meldungsfeld angezeigt.  
  
    ```c#  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
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
  
## Testen der MRU\-Liste  
  
#### So testen Sie die Liste der zuletzt verwendeten\-Menü  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debuggen  
  
2.  Auf der **TestMenu** Menü klicken Sie auf **aufrufen TestCommand**. Auf diese Weise zeigt ein Meldungsfeld an, der angibt, dass der Befehl aktiviert wurde.  
  
    > [!NOTE]
    >  Dieser Schritt ist erforderlich, erzwingen Sie das VSPackage geladen und die MRU\-Liste ordnungsgemäß angezeigt. Wenn Sie diesen Schritt überspringen, wird die MRU\-Liste nicht angezeigt.  
  
3.  Auf der **Testmenü** Menü klicken Sie auf **Untermenü**. Eine Liste mit vier Elementen wird am Ende der im Untermenü unter eine Trennlinie angezeigt. Beim Klicken auf **Element 3**, ein Meldungsfeld angezeigt werden soll, und zeigen Sie den Text "ausgewählte Element 3". \(Wenn die Liste der vier Elemente nicht angezeigt wird, stellen Sie sicher, dass Sie die Anweisungen im vorherigen Schritt ausgeführt haben.\)  
  
4.  Öffnen Sie das Untermenü erneut ein. Beachten Sie, dass **Element 3** ist nun am Anfang der Liste und die anderen Elemente haben eine Position nach unten verschoben wurde. Klicken Sie auf **Element 3** erneut aus und achten Sie darauf, die immer noch das Meldungsfeld zeigt "ausgewählte Element 3" gibt an, dass der Text korrekt an die neue Position zusammen mit der Bezeichnung Befehl verschoben wurde.  
  
## Siehe auch  
 [Dynamisches Hinzufügen von Menüelementen](../extensibility/dynamically-adding-menu-items.md)