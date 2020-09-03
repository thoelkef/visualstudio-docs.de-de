---
title: Hinzufügen eines Menüs zur Menüleiste | Microsoft-Dokumentation
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
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184929"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Hinzufügen eines Menüs zur Visual Studio-Menüleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein Menü zur Menüleiste der integrierten Entwicklungsumgebung (IDE) von Visual Studio hinzufügen. Die IDE-Menüleiste enthält Menü Kategorien wie z. b. **Datei**, **Bearbeiten**, **Ansicht**, **Fenster**und **Hilfe**.

 Bevor Sie der Visual Studio-Menüleiste ein neues Menü hinzufügen, sollten Sie überprüfen, ob die Befehle in einem vorhandenen Menü platziert werden sollen. Weitere Informationen zur Befehls Platzierung finden Sie unter [Menüs und Befehle für Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Menüs werden in der vsct-Datei des Projekts deklariert. Weitere Informationen zu Menüs und vsct-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

 Wenn Sie diese exemplarische Vorgehensweise durcharbeiten, können Sie ein Menü mit dem Namen **testmenu** erstellen, das einen Befehl enthält.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Erstellen eines VSIX-Projekts, das über eine benutzerdefinierte Befehls Element Vorlage verfügt

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `TopLevelMenu` . Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** " unter **Visual c#**-  /  **Erweiterbarkeit**.  Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **TestCommand**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#/Erweiterbarkeit** , und wählen Sie **benutzerdefinierter Befehl**aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Erstellen eines Menüs auf der IDE-Menüleiste

#### <a name="to-create-a-menu"></a>So erstellen Sie ein Menü

1. Öffnen Sie in **Projektmappen-Explorer**die Datei "testcommandpackage. vsct".

     Am Ende der Datei befindet sich ein \<Symbols> Knoten, der mehrere \<GuidSymbol> Knoten enthält. Fügen Sie im Knoten guidtestcommandpackagecmdset wie folgt ein neues Symbol hinzu:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. Erstellen Sie \<Menus> direkt zuvor einen leeren Knoten im \<Commands> Knoten \<Groups> . \<Menus>Fügen Sie im-Knoten \<Menu> wie folgt einen-Knoten hinzu:

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

     Der `guid` -Wert und der- `id` Wert des Menüs geben den Befehlssatz und das jeweilige Menü im Befehlssatz an.

     Die `guid` -und-Werte der über `id` geordneten positionieren das Menü im-Abschnitt der Visual Studio-Menüleiste, die die Menüs Tools und Add-Ins enthält.

     Der Wert der `CommandName` Zeichenfolge gibt an, dass der Text im Menü Element angezeigt werden soll.

3. Suchen Sie im \<Groups> \<Group> -Abschnitt nach, und ändern Sie das-Element so, dass \<Parent> es auf das soeben hinzugefügte Menü verweist:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Dadurch wird der Gruppen Teil des neuen Menüs.

4. Suchen Sie nach dem Abschnitt `Buttons`. Beachten Sie, dass die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Paket Vorlage ein-Element generiert hat `Button` , dessen übergeordnetes Element auf festgelegt ist `MyMenuGroup` . Daher wird dieser Befehl im Menü angezeigt.

## <a name="building-and-testing-the-extension"></a>Entwickeln und Testen der Erweiterung

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Eine Instanz der experimentellen Instanz sollte angezeigt werden.

2. Die Menüleiste in der experimentellen Instanz sollte ein **testmenu** -Menü enthalten.

3. Klicken Sie im Menü **Testmenü** auf **Test Befehl aufrufen**.

     Es sollte ein Meldungs Feld angezeigt werden, in dem die Meldung "TestCommand-Paket in toplevelmenu. TestCommand. MenuItemCallBack ()" angezeigt wird. Dies gibt an, dass der neue Befehl funktioniert.

## <a name="see-also"></a>Weitere Informationen
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
