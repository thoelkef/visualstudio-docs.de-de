---
title: Hinzufügen einer zuletzt verwendeten Liste zu einem Untermenü | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740298"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Hinzufügen einer zuletzt verwendeten Liste zu einem Untermenü
Diese exemplarische Vorgehensweise baut auf den Demos unter [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)auf und zeigt, wie sie einem Untermenü eine dynamische Liste hinzufügen. Die dynamische Liste bildet die Grundlage für die Erstellung einer Liste der zuletzt verwendeten Personen (MRU).

Eine dynamische Menüliste beginnt mit einem Platzhalter in einem Menü. Jedes Mal, wenn das Menü angezeigt wird, fragt die integrierte Visual Studio-Entwicklungsumgebung (IDE) das VSPackage nach allen Befehlen, die auf dem Platzhalter angezeigt werden sollen. Eine dynamische Liste kann überall in einem Menü auftreten. Dynamische Listen werden jedoch in der Regel selbst in Untermenüs oder am unteren Rand der Menüs gespeichert und angezeigt. Mithilfe dieser Entwurfsmuster aktivieren Sie die dynamische Liste der Befehle, die erweitert und zusammengegegenteilt werden können, ohne die Position anderer Befehle im Menü zu beeinflussen. In dieser exemplarischen Vorgehensweise wird die dynamische MRU-Liste am unteren Rand eines vorhandenen Untermenüs angezeigt, das durch eine Zeile vom Rest des Untermenüs getrennt ist.

Technisch kann eine dynamische Liste auch auf eine Symbolleiste angewendet werden. Wir raten jedoch davon ab, diese Verwendung zu verwenden, da eine Symbolleiste unverändert bleiben sollte, es sei denn, der Benutzer unternimmt bestimmte Schritte, um sie zu ändern.

In dieser exemplarischen Vorgehensweise wird eine MRU-Liste mit vier Elementen erstellt, die ihre Reihenfolge jedes Mal ändern, wenn eines von ihnen ausgewählt wird (das ausgewählte Element wird an den Anfang der Liste verschoben).

Weitere Informationen zu Menüs und *.vsct-Dateien* finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Voraussetzungen
Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Erstellen einer Erweiterung

- Gehen Sie wie folgt vor, um das Untermenü [zu](../extensibility/adding-a-submenu-to-a-menu.md) erstellen, das in den folgenden Verfahren geändert wird.

  Bei den Prozeduren in dieser exemplarischen Vorgehensweise `TopLevelMenu`wird davon ausgegangen, dass der Name des VSPackage der Name ist, der in [Der Visual Studio-Menüleiste ein Menü hinzufügen](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)verwendet wird.

## <a name="create-a-dynamic-item-list-command"></a>Erstellen eines dynamischen Elementlistenbefehls

1. Öffnen Sie *TestCommandPackage.vsct*.

2. Fügen `Symbols` Sie im `GuidSymbol` Abschnitt guidTestCommandPackageCmdSet das Symbol für `MRUListGroup` die `cmdidMRUList` Gruppe und den Befehl wie folgt hinzu.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Fügen `Groups` Sie im Abschnitt die deklarierte Gruppe nach den vorhandenen Gruppeneinträgen hinzu.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. Fügen `Buttons` Sie im Abschnitt einen Knoten hinzu, um den neu deklarierten Befehl nach den vorhandenen Schaltflächeneinträgen darzustellen.

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

    Mit `DynamicItemStart` dem Flag kann der Befehl dynamisch generiert werden.

5. Erstellen Sie das Projekt, und beginnen Sie mit dem Debuggen, um die Anzeige des neuen Befehls zu testen.

    Klicken Sie im **Menü TestMenu** auf das neue Untermenü, **Untermenü**, um den neuen Befehl **MRU-Platzhalter**anzuzeigen. Nachdem im nächsten Verfahren eine dynamische MRU-Liste von Befehlen implementiert wurde, wird diese Befehlsbezeichnung jedes Mal, wenn das Untermenü geöffnet wird, durch diese Liste ersetzt.

## <a name="filling-the-mru-list"></a>Ausfüllen der MRU-Liste

1. Fügen Sie in *TestCommandPackageGuids.cs*die folgenden Zeilen nach `TestCommandPackageGuids` den vorhandenen Befehls-IDs in der Klassendefinition hinzu.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. Fügen *Sie in TestCommand.cs* die folgende Usingsanweisung hinzu.

    ```csharp
    using System.Collections;
    ```

3. Fügen Sie den folgenden Code nach dem letzten AddCommand-Aufruf im TestCommand-Konstruktor hinzu. Die `InitMRUMenu` wird später definiert

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Fügen Sie den folgenden Code in der TestCommand-Klasse hinzu. Dieser Code initialisiert die Liste der Zeichenfolgen, die die Elemente darstellen, die in der MRU-Liste angezeigt werden sollen.

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

5. Fügen `InitializeMRUList` Sie nach `InitMRUMenu` der Methode die Methode hinzu. Dadurch werden die MRU-Listenmenübefehle initialisiert.

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

    Sie müssen für jedes mögliche Element in der MRU-Liste ein Menübefehlsobjekt erstellen. Die IDE `OnMRUQueryStatus` ruft die Methode für jedes Element in der MRU-Liste auf, bis keine weiteren Elemente mehr vorhanden sind. Im verwalteten Code besteht die einzige Möglichkeit für die IDE, zu wissen, dass es keine weiteren Elemente gibt, darin, zuerst alle möglichen Elemente zu erstellen. Wenn Sie möchten, können Sie zusätzliche Elemente zunächst `mc.Visible = false;` als nicht sichtbar markieren, indem Sie den Menübefehl verwenden. Diese Elemente können dann später `mc.Visible = true;` durch `OnMRUQueryStatus` Verwendung in der Methode sichtbar gemacht werden.

6. Fügen `InitMRUMenu` Sie nach der `OnMRUQueryStatus` Methode die folgende Methode hinzu. Dies ist der Handler, der den Text für jedes MRU-Element festlegt.

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

7. Fügen `OnMRUQueryStatus` Sie nach der `OnMRUExec` Methode die folgende Methode hinzu. Dies ist der Handler für die Auswahl eines MRU-Elements. Diese Methode verschiebt das ausgewählte Element an den Anfang der Liste und zeigt dann das ausgewählte Element in einem Meldungsfeld an.

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

1. Erstellen Sie das Projekt, und starten Sie das Debugging.

2. Klicken Sie im **Menü TestMenu** auf **TestCommand aufrufen**. Hier wird ein Meldungsfeld angezeigt, das angibt, dass der Befehl ausgewählt wurde.

    > [!NOTE]
    > Dieser Schritt ist erforderlich, um das VSPackage zum Laden zu zwingen und die MRU-Liste korrekt anzuzeigen. Wenn Sie diesen Schritt überspringen, wird die MRU-Liste nicht angezeigt.

3. Klicken Sie im Menü **testmenü** auf **Untermenü**. Eine Liste von vier Elementen wird am Ende des Untermenüs unterhalb eines Trennzeichens angezeigt. Wenn Sie auf **Element 3**klicken, sollte ein Meldungsfeld angezeigt werden, das den Text **"Ausgewähltes Element 3**" anzeigt. (Wenn die Liste der vier Elemente nicht angezeigt wird, stellen Sie sicher, dass Sie die Anweisungen im vorherigen Schritt befolgt haben.)

4. Öffnen Sie das Untermenü erneut. Beachten Sie, dass **Artikel 3** jetzt ganz oben in der Liste steht und die anderen Elemente um eine Position nach unten gedrückt wurden. Klicken Sie erneut auf **Element 3,** und beachten Sie, dass im Meldungsfeld weiterhin **ausgewähltes Element 3**angezeigt wird, was darauf hinweist, dass der Text zusammen mit der Befehlsbezeichnung korrekt an die neue Position verschoben wurde.

## <a name="see-also"></a>Weitere Informationen
- [Dynamisches Hinzufügen von Menüelementen](../extensibility/dynamically-adding-menu-items.md)
