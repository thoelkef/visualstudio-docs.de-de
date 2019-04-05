---
title: Hinzufügen einer zuletzt verwendete Liste aus, um ein Untermenü | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 47
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cf4f94d7459344353261b15552a51d9bb0f09e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957293"
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Hinzufügen einer Liste „Zuletzt verwendet“ zu einem Untermenü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise baut auf Demonstrationen in [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md), und zeigt, wie Sie eine dynamische Liste zu einem Untermenü hinzufügen. Liste mit der dynamische bildet die Grundlage zum Erstellen einer Liste der zuletzt verwendeten (MRU).  
  
 Eine dynamische Menüliste beginnt mit einem Platzhalter in einem Menü. Jedes Mal, wenn Sie im Menü angezeigt wird, fragt die integrierte Entwicklungsumgebung (IDE) von Visual Studio das VSPackage für alle Befehle, die auf den Platzhalter angezeigt werden soll. Eine dynamische Liste kann eine beliebige Stelle in einem Menü auftreten. Dynamische Listen sind jedoch in der Regel gespeichert und selbst angezeigt wird, Untermenüs oder auf die Spitzen des Menüs. Verwenden Sie diese Entwurfsmuster, können Sie die dynamische Liste der Befehle aus, um die Erweiterung und Verkleinerung ohne Auswirkungen auf die Position der anderen Befehle in diesem Menü aus. In dieser exemplarischen Vorgehensweise wird die dynamische MRU-Liste am unteren Rand einer vorhandenen Untermenü, das getrennt vom Rest des Untermenüs durch eine Linie angezeigt.  
  
 Technisch gesehen kann eine dynamische Liste auch zu einer Symbolleiste angewendet werden. Allerdings raten wir, dass Verwendungsdaten ab, da eine Symbolleiste unverändert bleiben soll, wenn der Benutzer eine bestimmte Schritte ändern ausführt.  
  
 In dieser exemplarischen Vorgehensweise erstellt eine MRU-Liste von vier Elementen, die die Reihenfolge zu ändern, jedes Mal, dass eine von ihnen ausgewählt ist (das ausgewählte Element wird am Anfang der Liste).  
  
 Weitere Informationen zu Menüs und VSCT-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Erstellen einer Erweiterung  
  
- Führen Sie die Verfahren in [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md) erstellen Sie in den folgenden Verfahren das Untermenü, das geändert wurde.  
  
  Die Verfahren in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Name des VSPackage `TopLevelMenu`, dies ist der Name, der verwendet wird [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Erstellen einen dynamischen Elementbefehl Liste  
  
1.  Öffnen Sie TestCommandPackage.vsct.  
  
2.  In der `Symbols` im Abschnitt der `GuidSymbol` Knoten mit dem Namen GuidTestCommandPackageCmdSet, fügen Sie das Symbol für die `MRUListGroup` Gruppe und die `cmdidMRUList` Befehl wie folgt.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  In der `Groups` Abschnitt fügen Sie der Gruppe "deklarierten" nach die vorhandenen Gruppeneinträge hinzu.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  In der `Buttons` Abschnitt, fügen Sie einen Knoten, um den neu deklarierten Befehl ein, nach der vorhandenen Schaltfläche Einträge darstellen.  
  
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
  
     Die `DynamicItemStart` Flag mit dem Befehl dynamisch generiert werden kann.  
  
5.  Erstellen Sie des Projekts, und starten Sie das Debuggen, um die Anzeige von den neuen Befehl zu testen.  
  
     Auf der **TestMenu** Menü klicken Sie auf die neue Untermenü **Untermenü**, um den neuen Befehl anzuzeigen **MRU-Platzhalter**. Nachdem eine dynamische MRU-Liste der Befehle in der nächsten Prozedur implementiert wird, wird diese Bezeichnung Befehl durch die Liste jedes Mal ersetzt, die das Untermenü geöffnet wird.  
  
## <a name="filling-the-mru-list"></a>Ausfüllen der MRU-Liste  
  
1.  Fügen Sie die folgenden Zeilen in TestCommandPackageGuids.cs, nachdem die vorhandenen Befehls-IDs in die `TestCommandPackageGuids` Definition der Klasse.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  TestCommand.cs fügen die folgende using-Anweisung.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Fügen Sie den folgenden Code im Konstruktor TestCommand, nach dem letzten AddCommand-Aufruf. Die `InitMRUMenu` später definiert werden  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Fügen Sie den folgenden Code in der TestCommand-Klasse. Dieser Code initialisiert die Liste der Zeichenfolgen, die darstellen, die Elemente auf der MRU-Liste angezeigt werden sollen.  
  
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
  
5.  Nach der `InitializeMRUList` -Methode hinzufügen der `InitMRUMenu` Methode. Dadurch wird die Menübefehle der MRU-Liste initialisiert.  
  
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
  
     Sie müssen ein Menü Command-Objekt für jedes mögliche Element in der MRU-Liste erstellen. Die IDE-Aufrufe der `OnMRUQueryStatus` Methode für jedes Element in der MRU-Liste, bis keine weiteren Elemente vorhanden sind. Die einzige Möglichkeit für die IDE zu wissen, dass keine weiteren Elemente vorhanden sind werden in verwaltetem Code erstellen Sie zunächst alle mögliche Elementen zu erstellen. Wenn Sie möchten, können Sie zusätzliche Elemente als nicht sichtbar ist, am zuerst markieren, mithilfe von `mc.Visible = false;` nach der Erstellung des Menübefehls. Diese Elemente können dann sichtbar gemacht werden später mithilfe von `mc.Visible = true;` in die `OnMRUQueryStatus` Methode.  
  
6.  Nach der `InitMRUMenu` -Methode, fügen Sie die folgenden `OnMRUQueryStatus` Methode. Dies ist der Handler, der den Text für jedes Element der MRU-Menü der legt diesen fest.  
  
    ```csharp  
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
  
7.  Nach der `OnMRUQueryStatus` -Methode, fügen Sie die folgenden `OnMRUExec` Methode. Dies ist der Handler für ein Element der MRU-Menü auswählen. Diese Methode verschiebt das ausgewählte Element an den Anfang der Liste, und klicken Sie dann das ausgewählte Element in einem Meldungsfeld angezeigt.  
  
    ```csharp  
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
  
## <a name="testing-the-mru-list"></a>Testen der MRU-Liste  
  
#### <a name="to-test-the-mru-menu-list"></a>So testen Sie die Liste der zuletzt verwendeten Menü  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debuggen  
  
2.  Auf der **TestMenu** Menü klicken Sie auf **aufrufen TestCommand**. Dies zeigt ein Meldungsfeld an, der angibt, dass es sich bei der Auswahl des Befehls.  
  
    > [!NOTE]
    >  Dieser Schritt ist erforderlich, um das VSPackage zu laden und Anzeigen von der MRU-Liste ordnungsgemäß zu erzwingen. Wenn Sie diesen Schritt überspringen, wird die MRU-Liste nicht angezeigt.  
  
3.  Auf der **Testmenü** Menü klicken Sie auf **Untermenü**. Eine Liste mit vier Elementen wird am Ende der im Untermenü unter ein Trennzeichen angezeigt. Beim Klicken auf **Element 3**, ein Meldungsfeld angezeigt werden soll, und der Text, "Ausgewählte Element 3" angezeigt. (Wenn die Liste der vier Elemente nicht angezeigt wird, stellen Sie sicher, dass Sie die Anweisungen im vorherigen Schritt ausgeführt haben.)  
  
4.  Öffnen Sie das Untermenü erneut ein. Beachten Sie, dass **Element 3** ist jetzt am oberen Rand der Liste und die anderen Elemente haben eine Position nach unten verschoben wurde. Klicken Sie auf **Element 3** erneut aus, und beachten Sie, dass zeigt das Meldungsfeld noch "Ausgewählte Element 3", der angibt, dass der Text ordnungsgemäß auf die neue Position zusammen mit der Bezeichnung Befehl verschoben wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamisches Hinzufügen von Menüelementen](../extensibility/dynamically-adding-menu-items.md)
