---
title: "Hinzuf&#252;gen einer Symbolleiste | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbolleisten [Visual Studio], zur IDE hinzufügen"
  - "IDE, Symbolleisten hinzufügen"
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# Hinzuf&#252;gen einer Symbolleiste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Visual Studio\-IDE eine Symbolleiste hinzugefügt.  
  
 Eine Symbolleiste ist eine horizontale oder vertikale Leiste mit Schaltflächen, die Befehle gebunden sind. Je nach der Implementierung kann eine Symbolleiste in der IDE werden neu angeordnet, am Rand des IDE\-Hauptfenster angedockt oder Vordergrund bleiben vorgenommen.  
  
 Darüber hinaus können Benutzer hinzufügen von Befehlen zu einer Symbolleiste oder über daraus entfernen der **Anpassen** \(Dialogfeld\). In der Regel sind Symbolleisten in VSPackages benutzerdefinierbare. Die IDE verarbeitet alle Anpassung und das VSPackage reagiert auf. Das VSPackage muss nicht wissen, wo sich ein Befehl physisch befindet.  
  
 Weitere Informationen zu den Menüs, finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eine Erweiterung mit einer Symbolleiste  
 Erstellen Sie ein VSIX\-Projekt namens `IDEToolbar`. Hinzufügen eine Menü Befehl Elementvorlage, die mit dem Namen **ToolbarTestCommand**. Informationen hierzu finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Zum Erstellen einer Symbolleiste für die IDE  
  
1.  Suchen Sie in ToolbarTestCommandPackage.vsct den Abschnitt "Symbole". Fügen Sie im GuidSymbol\-Element mit dem Namen GuidToolbarTestCommandPackageCmdSet Deklarationen für eine Symbolleiste und einer Symbolleistengruppe folgendermaßen ein:  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  Klicken Sie oben im Abschnitt Befehle erstellen Sie einen Abschnitt des Menüs. Fügen Sie ein Menüelement Abschnitt Menüs auf die Symbolleiste zu definieren.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     Symbolleisten können wie Untermenüs geschachtelt werden. Daher müssen Sie nicht in der übergeordneten Gruppe zuweisen. Darüber hinaus müssen Sie keine Priorität festlegen, da der Benutzer Symbolleisten verschieben kann. In der Regel erste Platzierung einer Symbolleiste programmgesteuert definiert ist, aber nachfolgende Änderungen vom Benutzer beibehalten werden.  
  
3.  In der [Gruppen](../extensibility/groups-element.md) Abschnitt nach der vorhandenen Gruppe Eintrag Definieren einer [Gruppe](../extensibility/group-element.md) Element die Befehle für die Symbolleiste enthält.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Stellen Sie die Schaltfläche auf der Symbolleiste angezeigt. Ersetzen Sie den übergeordneten Block in der Schaltfläche auf der Symbolleiste im Abschnitt Schaltflächen. Die daraus resultierenden Befehlsblock Schaltfläche sollte wie folgt aussehen:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     In der Standardeinstellung Wenn eine Symbolleiste keine Befehle, wird es nicht angezeigt.  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
6.  Mit der rechten Maustaste in der Visual Studio\-Menüleiste zum Abrufen der Liste der Symbolleisten. Wählen Sie **Symbolleiste**.  
  
7.  Die Symbolleiste sollte jetzt als Symbol rechts neben der Suche in Dateien Symbol angezeigt werden. Wenn Sie auf das Symbol klicken, sollte ein Meldungsfeld mit der Meldung **ToolbarTestCommandPackage. In IDEToolbar.ToolbarTestCommand.MenuItemCallback\(\)**.  
  
## Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)