---
title: Hinzufügen eines Menüs zur Menüleiste Menüpunkt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 255afb948f7a7e00f1249c332eac7234800ae980
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961397"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Hinzufügen eines Menüs zur Visual Studio-Menüleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise zeigt, wie ein Menü zur von der integrierten Entwicklungsumgebung (IDE) von Visual Studio-Menüleiste hinzugefügt wird. Die IDE-Menüleiste enthält Menükategorien wie z. B. **Datei**, **bearbeiten**, **Ansicht**, **Fenster**, und **Hilfe** .

 Hinzufügen eines neuen Menüs zur Menüleiste Visual Studio, berücksichtigen Sie, ob Ihre Befehle in einem vorhandenen Menü eingefügt werden soll. Weitere Informationen zur Platzierung der Befehl finden Sie unter [Menüs und Befehle für Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Menüs werden in der VSCT-Datei des Projekts deklariert. Weitere Informationen zu Menüs und VSCT-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

 Diese exemplarische Vorgehensweise durcharbeiten, können Sie ein Menü mit dem Namen erstellen **TestMenu** , das einen Befehl enthält.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Erstellen eines VSIX-Projekts mit einer benutzerdefinierten Befehls-Elementvorlage

1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TopLevelMenu`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual C#-** / **Erweiterbarkeit**.  Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2.  Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **TestCommand**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Erstellen eines Menüs in der IDE-Menüleiste

#### <a name="to-create-a-menu"></a>Zum Erstellen eines Menüs

1.  In **Projektmappen-Explorer**, TestCommandPackage.vsct zu öffnen.

     Am Ende der Datei, besteht eine \<Symbole > Knoten, der mehrere enthält \<GuidSymbol > Knoten. Fügen Sie ein neues Symbol, klicken Sie im Knoten mit dem Namen GuidTestCommandPackageCmdSet wie folgt:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2.  Erstellen Sie eine leere \<Menüs > Knoten in der \<Befehle > Knoten direkt vor \<Gruppen >. In der \<Menüs > Knoten Hinzufügen einer \<Menü > Knoten wie folgt:

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

3.  In der \<Gruppen > im Abschnitt, finden Sie die \<Gruppe >, und ändern Sie die \<übergeordneten >-Elements auf das Menü zeigen wir gerade hinzugefügt haben:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Dadurch wird den Teil von Gruppe für das neue Menü.

4.  Suchen der `Buttons` Abschnitt. Beachten Sie, dass die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Paket-Vorlage wurde generiert eine `Button` -Element, das das übergeordnete Element festgelegt wurde `MyMenuGroup`. Mit diesem Befehl wird daher in Ihrem Menü angezeigt.

## <a name="building-and-testing-the-extension"></a>Erstellen und testen die Erweiterung

1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Eine Instanz der experimentellen Instanz sollten angezeigt werden.

2.  Die Menüleiste in der experimentellen Instanz sollte enthalten eine **TestMenu** Menü.

3.  Auf der **TestMenu** Menü klicken Sie auf **Test-Invoke-Command**.

     Ein Meldungsfeld angezeigt werden soll, und die Meldung "Paket in TopLevelMenu.TestCommand.MenuItemCallback() TestCommand" angezeigt. Dies gibt an, dass der neue Befehl funktioniert.

## <a name="see-also"></a>Siehe auch
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
