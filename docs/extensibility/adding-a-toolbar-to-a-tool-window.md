---
title: Ein Toolfenster eine Symbolleiste hinzugefügt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47ff5f69ff559ea1c08d0ae9bdd7192a257c844e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Ein Toolfenster hinzugefügt eine Symbolleiste
In dieser exemplarischen Vorgehensweise wird gezeigt, wie einem Toolfenster eine Symbolleiste hinzugefügt wird.  
  
 Eine Symbolleiste ist einer horizontalen oder vertikalen Leiste, die Schaltflächen Befehlen gebunden sind. Die Länge einer Symbolleiste in einem Toolfenster entspricht immer dem als die Breite oder Höhe des Toolfensters, je nachdem, wo die Symbolleiste angedockt ist.  
  
 Im Gegensatz zu Symbolleisten in der IDE muss eine Symbolleiste in einem Toolfenster angedockt und kann nicht verschoben oder angepasst. Wenn das VSPackage in Umanaged Code geschrieben ist, können Sie die Symbolleiste auf keinem Rand angedockt.  
  
 Weitere Informationen zum Hinzufügen einer Symbolleiste finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Zum Erstellen einer Symbolleiste für ein Toolfenster  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TWToolbar` , besitzt sowohl einen Menübefehl, mit dem Namen **TWTestCommand** und ein Toolfenster namens **TestToolWindow**. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) und [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md). Sie müssen die Elementvorlage Befehl vor dem Hinzufügen einer Vorlage für das Tool-Fenster hinzufügen.  
  
2.  Suchen Sie in TWTestCommandPackage.vsct für den Abschnitt Symbole. Deklarieren Sie im Knoten "GuidSymbol" mit dem Namen GuidTWTestCommandPackageCmdSet eine Symbolleiste und eine Symbolleistengruppe wie folgt.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  Am oberen Rand der `Commands` Abschnitt, erstellen Sie eine `Menus` Abschnitt. Hinzufügen einer `Menu` Element auf die Symbolleiste zu definieren.  
  
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
  
     Symbolleisten können z. B. Untermenüs geschachtelt werden. Aus diesem Grund müssen Sie kein übergeordnetes Element zuzuweisen. Darüber hinaus müssen Sie keine Priorität festlegen, da der Benutzer die Symbolleisten verschieben kann. In der Regel anfängliche Platzierung einer Symbolleiste wird programmgesteuert definiert, aber nachfolgende Änderungen durch den Benutzer werden beibehalten.  
  
4.  Definieren Sie im Abschnitt Gruppen eine Gruppe, um die Befehle für die Symbolleiste enthalten.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  Ändern Sie das übergeordnete Element des vorhandenen Button-Element im Abschnitt Schaltflächen auf der Symbolleistengruppe, sodass die Symbolleiste angezeigt wird.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Standardmäßig Wenn eine Symbolleiste keine Befehle, wird es nicht angezeigt.  
  
     Da die neue Symbolleiste nicht automatisch zum Toolfenster hinzugefügt wird, muss die Symbolleiste explizit hinzugefügt werden. Dies wird im nächsten Abschnitt erläutert.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Hinzufügen der Symbolleiste auf das Toolfenster  
  
1.  Fügen Sie in TWTestCommandPackageGuids.cs die folgenden Zeilen hinzu.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  Fügen Sie TestToolWindow.cs folgende Anweisung verwenden.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  Fügen Sie die folgende Zeile in der TestToolWindow-Konstruktor.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Testen die Symbolleiste im Toolfenster  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.  
  
2.  Auf der **Ansicht / Weitere Fenster** Menü klicken Sie auf **Test (Toolfenster)** das Toolfenster angezeigt.  
  
     Sollte angezeigt werden, dass eine Symbolleiste (sie sieht wie das Standardsymbol) am Anfang des Toolfensters direkt unterhalb der Titel links.  
  
3.  Klicken Sie auf der Symbolleiste auf das Symbol, um die Nachricht anzuzeigen **TWTestCommandPackage in TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)