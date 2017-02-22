---
title: "Ein Toolfenster hinzugef&#252;gt eine Symbolleiste | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolfenster, Hinzufügen von Symbolleisten"
  - "Symbolleisten [Visual Studio] Toolfenster hinzufügen"
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 48
caps.handback.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
---
# Ein Toolfenster hinzugef&#252;gt eine Symbolleiste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise veranschaulicht, wie Sie ein Toolfenster eine Symbolleiste hinzufügen.  
  
 Eine Symbolleiste ist eine horizontale oder vertikale Streifen, der Schaltflächen an Befehle gebunden sind. Die Länge einer Symbolleiste in einem Toolfenster ist immer identisch mit der Breite oder Höhe des Toolfensters, je nachdem, wo die Symbolleiste angedockt wird.  
  
 Im Gegensatz zu den Symbolleisten in der IDE muss eine Symbolleiste in einem Toolfenster angedockt werden kann nicht verschoben oder angepasst. Wenn das VSPackage Umanaged Code geschrieben ist, kann die Symbolleiste auf eine Kante angedockt werden.  
  
 Weitere Informationen zum Hinzufügen einer Symbolleiste finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Zum Erstellen einer Symbolleiste für ein Toolfenster  
  
1.  Erstellen Sie ein VSIX\-Projekt namens `TWToolbar` bei dem beide einen Menübefehl mit dem Namen **TWTestCommand** und ein Fenster mit dem Namen **TestToolWindow**. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) und [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md). Sie müssen die Elementvorlage Befehl vor dem Hinzufügen der Tool\-Fenster\-Vorlage hinzufügen.  
  
2.  Suchen Sie in TWTestCommandPackage.vsct den Abschnitt "Symbole". In der GuidSymbol\-Knoten mit dem Namen GuidTWTestCommandPackageCmdSet Deklarieren einer Symbolleiste und einer Symbolleistengruppe wie folgt.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  Am oberen Rand der `Commands` im Abschnitt, erstellen Sie ein `Menus` Abschnitt. Hinzufügen einer `Menu` \-Element zum Definieren der Symbolleiste.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Symbolleisten können wie Untermenüs geschachtelt werden. Daher müssen Sie kein übergeordnetes Element zugewiesen. Darüber hinaus müssen Sie keine Priorität festlegen, da der Benutzer Symbolleisten verschieben kann. In der Regel erste Platzierung einer Symbolleiste programmgesteuert definiert ist, aber nachfolgende Änderungen vom Benutzer beibehalten werden.  
  
4.  Definieren Sie im Abschnitt Gruppen eine Gruppe, die Befehle für die Symbolleiste enthält.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  Ändern Sie im Abschnitt Schaltflächen das übergeordnete Element des vorhandenen Button\-Element in der Symbolleistengruppe, sodass die Symbolleiste angezeigt wird.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     In der Standardeinstellung Wenn eine Symbolleiste keine Befehle, wird es nicht angezeigt.  
  
     Da die neue Symbolleiste im Toolfenster nicht automatisch hinzugefügt wird, muss die Symbolleiste explizit hinzugefügt werden. Dies wird im nächsten Abschnitt erläutert.  
  
## Hinzufügen der Symbolleiste im Toolfenster  
  
1.  Fügen Sie die folgenden Zeilen in TWTestCommandPackageGuids.cs.  
  
    ```c#  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  TestToolWindow.cs fügen Sie folgende using\-Anweisung.  
  
    ```c#  
    using System.ComponentModel.Design;  
    ```  
  
3.  Fügen Sie die folgende Zeile in der TestToolWindow\-Konstruktor.  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## Testen die Symbolleiste im Toolfenster  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.  
  
2.  Auf der **Anzeigen \/ andere Fenster** Menü klicken Sie auf **Test im** im Toolfenster angezeigt.  
  
     Sie sollten eine Symbolleiste \(es sieht wie das Standardsymbol\) am Anfang des Toolfensters, direkt unterhalb des Titels links sehen.  
  
3.  Klicken Sie auf der Symbolleiste auf das Symbol, um die Anzeige der **TWTestCommandPackage in TWToolbar.TWTestCommand.MenuItemCallback\(\)**.  
  
## Siehe auch  
 [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)