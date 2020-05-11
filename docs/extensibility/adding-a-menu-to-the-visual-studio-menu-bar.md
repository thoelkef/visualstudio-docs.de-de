---
title: Hinzufügen eines Menüs zur Visual Studio-Menüleiste | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740313"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Hinzufügen eines Menüs zur Visual Studio-Menüleiste

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie der Menüleiste der integrierten Visual Studio-Entwicklungsumgebung (IDE) ein Menü hinzufügen. Die IDE-Menüleiste enthält Menükategorien wie **Datei**, **Bearbeiten**, **Anzeigen**, **Fenster**und **Hilfe**.

Bevor Sie der Visual Studio-Menüleiste ein neues Menü hinzufügen, sollten Sie überlegen, ob ihre Befehle in einem vorhandenen Menü platziert werden sollen. Weitere Informationen zur [Befehlsplatzierung](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)finden Sie unter Menüs und Befehle für Visual Studio .

Menüs werden in der *.vsct-Datei* des Projekts deklariert. Weitere Informationen zu Menüs und *.vsct-Dateien* finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

Durch Abschließen dieser exemplarischen Vorgehensweise können Sie ein Menü mit dem Namen **TestMenu** erstellen, das einen Befehl enthält.

> [!NOTE]
> In VS 2019 werden Menüs der obersten Ebene, die von Erweiterungen beigesteuert werden, unter das Menü **Erweiterungen** platziert.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Erstellen eines VSIX-Projekts mit einer benutzerdefinierten Befehlselementvorlage

1. Erstellen Sie ein `TopLevelMenu`VSIX-Projekt mit dem Namen . Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.  Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehlselementvorlage mit dem Namen **TestCommand**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** >  aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C/ Erweiterbarkeit,** und wählen Sie **Benutzerdefinierter Befehl aus.** Ändern Sie im Feld **Name** am unteren Rand des Fensters den Befehlsdateinamen in *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Erstellen eines Menüs in der IDE-Menüleiste

::: moniker range="vs-2017"

1. Öffnen Sie im **Projektmappen-Explorer** *TestCommandPackage.vsct*.

    Am Ende der Datei befindet \<sich ein Symbol \<> Knoten, der mehrere GuidSymbol-> Knoten enthält. Fügen Sie im Knoten mit dem Namen guidTestCommandPackageCmdSet ein neues Symbol wie folgt hinzu:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Erstellen Sie \<ein leeres \<Menü> Knoten \<im Befehlsknoten> Knoten, kurz bevor Gruppen>. Fügen \<Sie im Knoten Menüs> einen \<Menüknoten> wie folgt hinzu:

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

    Die `guid` `id` werte des Menüs geben den Befehlssatz und das spezifische Menü im Befehlssatz an.

    Die `guid` `id` und die Werte des übergeordneten Elements positionieren das Menü im Abschnitt der Visual Studio-Menüleiste, der die Menüs Extras und Add-Ins enthält.

    Der Wert `CommandName` der Zeichenfolge gibt an, dass der Text im Menüelement angezeigt werden soll.

3. Suchen \<Sie im Abschnitt \<Gruppen> die \<Gruppe>, und ändern Sie das Element Parent>, um auf das Menü zu verweisen, das wir gerade hinzugefügt haben:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Dadurch wird die Gruppe Teil des neuen Menüs.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie im **Projektmappen-Explorer** *TopLevelMenuPackage.vsct*.

    Am Ende der Datei befindet \<sich ein Symbol \<> Knoten, der mehrere GuidSymbol-> Knoten enthält. Fügen Sie im Knoten mit dem Namen guidTopLevelMenuPackageCmdSet ein neues Symbol wie folgt hinzu:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Erstellen Sie \<ein leeres \<Menü> Knoten \<im Befehlsknoten> Knoten, kurz bevor Gruppen>. Fügen \<Sie im Knoten Menüs> einen \<Menüknoten> wie folgt hinzu:

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

    Die `guid` `id` werte des Menüs geben den Befehlssatz und das spezifische Menü im Befehlssatz an.

    Die `guid` `id` und die Werte des übergeordneten Elements positionieren das Menü im Abschnitt der Visual Studio-Menüleiste, der die Menüs Extras und Add-Ins enthält.

    Der Wert `CommandName` der Zeichenfolge gibt an, dass der Text im Menüelement angezeigt werden soll.

3. Suchen \<Sie im Abschnitt \<Gruppen> die \<Gruppe>, und ändern Sie das Element Parent>, um auf das Menü zu verweisen, das wir gerade hinzugefügt haben:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Dadurch wird die Gruppe Teil des neuen Menüs.

::: moniker-end

4. Suchen Sie nach dem Abschnitt `Buttons`. Beachten Sie, dass [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die `Button` Paketvorlage ein Element `MyMenuGroup`generiert hat, dessen übergeordnetes Element auf festgelegt ist. Daher wird dieser Befehl im Menü angezeigt.

## <a name="build-and-test-the-extension"></a>Erstellen und Testen der Erweiterung

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Eine Instanz der experimentellen Instanz sollte angezeigt werden.

::: moniker range="vs-2017"

2. Die Menüleiste in der experimentellen Instanz sollte ein **TestMenu-Menü** enthalten.

::: moniker-end

::: moniker range=">=vs-2019"

2. Das Menü **Erweiterungen** in der experimentellen Instanz sollte ein **TestMenu-Menü** enthalten.

::: moniker-end

3. Klicken Sie im **Menü TestMenu** auf **Testbefehl aufrufen**.

     Ein Meldungsfeld sollte angezeigt werden und die Meldung "TestCommand Package Inside TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Weitere Informationen

- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
