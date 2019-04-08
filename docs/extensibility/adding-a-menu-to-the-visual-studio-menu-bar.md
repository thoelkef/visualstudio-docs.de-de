---
title: Hinzufügen eines Menüs auf der Menüleiste von Visual Studio | Microsoft-Dokumentation
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7ce5ab06eb641e94d6f972b888882ac1e53e2ee
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58195046"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Hinzufügen eines Menüs zur Menüleiste Visual Studio

Diese exemplarische Vorgehensweise zeigt, wie ein Menü zur von der integrierten Entwicklungsumgebung (IDE) von Visual Studio-Menüleiste hinzugefügt wird. Die IDE-Menüleiste enthält Menükategorien wie z. B. **Datei**, **bearbeiten**, **Ansicht**, **Fenster**, und **Hilfe** .

Hinzufügen eines neuen Menüs zur Menüleiste Visual Studio, berücksichtigen Sie, ob Ihre Befehle in einem vorhandenen Menü eingefügt werden soll. Weitere Informationen zur Platzierung der Befehl finden Sie unter [Menüs und Befehle für Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Menüs werden in deklariert die *VSCT* -Datei des Projekts. Weitere Informationen zu Menüs und *VSCT* finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

Diese exemplarische Vorgehensweise durcharbeiten, können Sie ein Menü mit dem Namen erstellen **TestMenu** , das einen Befehl enthält.

> [!NOTE]
> In Visual Studio-2019 befinden die Menüs der obersten Ebene von Extensions beigetragen wurden unter der **Erweiterungen** Menü.

## <a name="prerequisites"></a>Vorraussetzungen

Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Erstellen Sie ein VSIX-Projekt, die eine benutzerdefinierten Befehl-Elementvorlage

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `TopLevelMenu`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld, indem Sie nach "Vsix" suchen.  Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **TestCommand**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** >  **neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Erstellen Sie ein Menüelement in der IDE-Menüleiste

::: moniker range="vs-2017"

1. In **Projektmappen-Explorer**öffnen *TestCommandPackage.vsct*.

    Am Ende der Datei, besteht eine \<Symbole > Knoten, der mehrere enthält \<GuidSymbol > Knoten. Fügen Sie ein neues Symbol, klicken Sie im Knoten mit dem Namen GuidTestCommandPackageCmdSet wie folgt:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Erstellen Sie eine leere \<Menüs > Knoten in der \<Befehle > Knoten direkt vor \<Gruppen >. In der \<Menüs > Knoten Hinzufügen einer \<Menü > Knoten wie folgt:

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

    Die `guid` und `id` Werte des Menüs Geben Sie den Befehlssatz, und bestimmte Menü in den Befehlssatz.

    Die `guid` und `id` Werte des übergeordneten Elements positionieren Sie im Menü auf der Teil der Visual Studio-Menüleiste, die die Tools und Add-Ins Menüs enthält.

    Der Wert des der `CommandName` Zeichenfolge gibt an, dass der Text im Menüelement angezeigt wird.

3. In der \<Gruppen > im Abschnitt, finden Sie die \<Gruppe >, und ändern Sie die \<übergeordneten >-Elements auf das Menü zeigen wir gerade hinzugefügt haben:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Dadurch wird den Teil von Gruppe für das neue Menü.

::: moniker-end

::: moniker range=">=vs-2019"

1. In **Projektmappen-Explorer**öffnen *TopLevelMenuPackage.vsct*.

    Am Ende der Datei, besteht eine \<Symbole > Knoten, der mehrere enthält \<GuidSymbol > Knoten. Fügen Sie ein neues Symbol, klicken Sie im Knoten mit dem Namen GuidTopLevelMenuPackageCmdSet wie folgt:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Erstellen Sie eine leere \<Menüs > Knoten in der \<Befehle > Knoten direkt vor \<Gruppen >. In der \<Menüs > Knoten Hinzufügen einer \<Menü > Knoten wie folgt:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Die `guid` und `id` Werte des Menüs Geben Sie den Befehlssatz, und bestimmte Menü in den Befehlssatz.

    Die `guid` und `id` Werte des übergeordneten Elements positionieren Sie im Menü auf der Teil der Visual Studio-Menüleiste, die die Tools und Add-Ins Menüs enthält.

    Der Wert des der `CommandName` Zeichenfolge gibt an, dass der Text im Menüelement angezeigt wird.

3. In der \<Gruppen > im Abschnitt, finden Sie die \<Gruppe >, und ändern Sie die \<übergeordneten >-Elements auf das Menü zeigen wir gerade hinzugefügt haben:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Dadurch wird den Teil von Gruppe für das neue Menü.

::: moniker-end

4. Suchen der `Buttons` Abschnitt. Beachten Sie, dass die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Paket-Vorlage wurde generiert eine `Button` -Element, das das übergeordnete Element festgelegt wurde `MyMenuGroup`. Daher wird Sie mit diesem Befehl in Ihrem Menü angezeigt.

## <a name="build-and-test-the-extension"></a>Erstellen Sie und Testen Sie die Erweiterung

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Eine Instanz der experimentellen Instanz sollten angezeigt werden.

::: moniker range="vs-2017"

2. Die Menüleiste in der experimentellen Instanz sollte enthalten eine **TestMenu** Menü.

::: moniker-end

::: moniker range=">=vs-2019"

2. Die **Erweiterungen** Menü in der experimentellen Instanz sollte enthalten eine **TestMenu** Menü.

::: moniker-end

3. Auf der **TestMenu** Menü klicken Sie auf **Test-Invoke-Command**.

     Ein Meldungsfeld angezeigt werden soll, und die Meldung "Paket in TopLevelMenu.TestCommand.MenuItemCallback() TestCommand" angezeigt.

## <a name="see-also"></a>Siehe auch

- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)