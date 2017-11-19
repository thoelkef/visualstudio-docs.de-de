---
title: "Hinzufügen eines Menüs auf der Menüleiste von Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: "51"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e4a2485b7e702844a037787234ef3a1ab66495d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Hinzufügen eines Menüs auf der Menüleiste von Visual Studio
In dieser exemplarischen Vorgehensweise wird gezeigt, wie ein Menü zur von der integrierten Entwicklungsumgebung (IDE) von Visual Studio-Menüleiste hinzugefügt. Die IDE-Menüleiste enthält Menükategorien, wie z. B. **Datei**, **bearbeiten**, **Ansicht**, **Fenster**, und **Hilfe** .  
  
 Vor dem Hinzufügen eines neuen Menüs zur Menüleiste Visual Studio, berücksichtigen Sie, ob Ihre Befehle in einem vorhandenen Menü platziert werden soll. Weitere Informationen zur Platzierung von Befehl finden Sie unter [Menüs und Befehle für Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Menüs sind in der VSCT-Datei des Projekts deklariert. Weitere Informationen über Menüs und VSCT-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Diese exemplarische Vorgehensweise durcharbeiten, können Sie ein Menü mit dem Namen erstellen **TestMenu** , die einem Befehl enthält.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Ein VSIX-Projekt erstellen, die eine benutzerdefinierten Befehl-Elementvorlage  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TopLevelMenu`. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual C#-** / **Erweiterbarkeit**.  Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage für benutzerdefinierte Befehl mit dem Namen **TestCommand**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Befehl**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **TestCommand.cs**.  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Erstellen eines Menüs in der IDE-Menüleiste  
  
#### <a name="to-create-a-menu"></a>Um ein Menü zu erstellen.  
  
1.  In **Projektmappen-Explorer**, TestCommandPackage.vsct zu öffnen.  
  
     Am Ende der Datei ist ein \<Symbole >-Knoten, mehrere enthält \<GuidSymbol > Knoten. Fügen Sie in den Knoten mit dem Namen GuidTestCommandPackageCmdSet ein neues Symbol wie folgt:  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Erstellen Sie eine leere \<Menüs > Knoten in der \<Befehle > Knoten unmittelbar vor dem \<Gruppen >. In der \<Menüs > Knoten Hinzufügen einer \<Menü > Knoten wie folgt:  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Die `guid` und `id` Werte des Menüs Geben Sie den Befehlssatz und des bestimmten Menüs in den Befehlssatz.  
  
     Die `guid` und `id` Werte des übergeordneten Elements positionieren Sie das Menü in der Teil der Visual Studio-Menüleiste, die die Tools und Add-Ins Menüs enthält.  
  
     Der Wert, der die `CommandName` Zeichenfolge gibt an, dass der Text in das Menüelement angezeigt werden soll.  
  
3.  In der \<Gruppen > aus, suchen Sie im Abschnitt der \<Gruppe >, und ändern Sie die \<übergeordneten >-Elements auf das Menü zeigen wir gerade hinzugefügt:  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     Dadurch wird die Gruppe Bestandteil des neuen Menüs.  
  
4.  Suchen der `Buttons` Abschnitt. Beachten Sie, dass die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paketvorlage wurde generiert eine `Button` Element mit seinem übergeordneten Element festgelegt `MyMenuGroup`. Mit diesem Befehl wird daher in Ihrem Menü angezeigt.  
  
## <a name="building-and-testing-the-extension"></a>Erstellen und Testen der Erweiterung  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Eine Instanz der experimentellen Instanz sollte angezeigt werden.  
  
2.  Die Menüleiste in der experimentellen Instanz sollte enthalten eine **TestMenu** Menü.  
  
3.  Auf der **TestMenu** Menü klicken Sie auf **Test Aufrufbefehl**.  
  
     Ein Meldungsfeld angezeigt werden soll, und die Meldung "TestCommand Paket innerhalb TopLevelMenu.TestCommand.MenuItemCallback()" angezeigt. Dies gibt an, dass der neue Befehl funktioniert.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)