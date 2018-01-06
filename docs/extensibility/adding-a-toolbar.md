---
title: "Hinzufügen einer Symbolleiste | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f7b837a620a1e116b9bb8a11ff8a4edab7bfabfb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-toolbar"></a>Hinzufügen einer Symbolleiste
In dieser exemplarischen Vorgehensweise wird gezeigt, wie der Visual Studio-IDE eine Symbolleiste hinzugefügt wird.  
  
 Eine Symbolleiste ist ein horizontaler oder vertikaler Bereichsstreifen mit Schaltflächen, die Befehle gebunden sind. Abhängig von der Implementierung kann eine Symbolleiste in der IDE neu angeordnet, auf jeder Seite des Hauptfensters der IDE angedockt sein vor anderen Fenstern bleiben vorgenommen.  
  
 Darüber hinaus können Benutzer Befehle hinzufügen, um eine Symbolleiste oder mithilfe von ihm Entfernen der **anpassen** (Dialogfeld). In der Regel sind Symbolleisten in VSPackages Benutzer anpassbar. Verarbeitet die IDE alle Anpassungen ein, und das VSPackage reagiert auf. Das VSPackage muss nicht wissen, in denen ein Befehl physisch befindet.  
  
 Weitere Informationen, Menüs, finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Erstellen eine Erweiterung mit einer Symbolleiste  
 Erstellen Sie ein VSIX-Projekt mit dem Namen `IDEToolbar`. Hinzufügen eine Menü Befehl Elementvorlage, die mit dem Namen **ToolbarTestCommand**. Informationen hierzu finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Zum Erstellen einer Symbolleiste für die IDE  
  
1.  Suchen Sie in ToolbarTestCommandPackage.vsct für den Abschnitt Symbole. Fügen Sie in das GuidSymbol-Element mit dem Namen GuidToolbarTestCommandPackageCmdSet Deklarationen für eine Symbolleiste und eine Symbolleistengruppe wie folgt ein.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  Klicken Sie oben im Abschnitt Befehle erstellen Sie einen Menüs-Abschnitt. Fügen Sie ein Menüelement im hinzu Menüs im Abschnitt zum Definieren der Symbolleiste angezeigt wird.  
  
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
  
     Symbolleisten können z. B. Untermenüs geschachtelt werden. Aus diesem Grund müssen Sie keine übergeordnete Gruppe zuweisen. Darüber hinaus müssen Sie keine Priorität festlegen, da der Benutzer die Symbolleisten verschieben kann. In der Regel anfängliche Platzierung einer Symbolleiste wird programmgesteuert definiert, aber nachfolgende Änderungen durch den Benutzer werden beibehalten.  
  
3.  In der [Gruppen](../extensibility/groups-element.md) Abschnitt nach der vorhandenen Gruppe Eintrag definieren eine [Gruppe](../extensibility/group-element.md) Element enthält die Befehle für die Symbolleiste.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Stellen Sie die Schaltfläche auf der Symbolleiste angezeigt. Ersetzen Sie im Abschnitt Schaltflächen den übergeordneten Block in der Schaltfläche auf der Symbolleiste aus. Der resultierende Schaltfläche-Block sollte wie folgt aussehen:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Standardmäßig Wenn eine Symbolleiste keine Befehle, wird es nicht angezeigt.  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
6.  Mit der rechten Maustaste in der Visual Studio-Menüleiste zum Abrufen der Liste der Symbolleisten. Wählen Sie **testen Symbolleiste**.  
  
7.  Die Symbolleiste sollte jetzt als Symbol rechts neben der Suche in Dateien Symbol angezeigt werden. Wenn Sie das Symbol klicken, sehen Sie ein Dialogfeld mit der Meldung **ToolbarTestCommandPackage. In IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)