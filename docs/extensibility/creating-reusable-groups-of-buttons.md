---
title: Wiederverwendbare Schaltflächengruppen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739463"
---
# <a name="create-reusable-groups-of-buttons"></a>Erstellen wiederverwendbarer Schaltflächengruppen
Eine Befehlsgruppe ist eine Sammlung von Befehlen, die immer zusammen in einem Menü oder einer Symbolleiste angezeigt werden. Jede Befehlsgruppe kann erneut verwendet werden, indem sie verschiedenen übergeordneten Menüs im Abschnitt CommandPlacements der *.vsct-Datei* zugewiesen wird.

 Befehlsgruppen enthalten in der Regel Schaltflächen, können aber auch andere Menüs oder Kombinationsfelder enthalten.

## <a name="to-create-a-reusable-group-of-buttons"></a>So erstellen Sie eine wiederverwendbare Gruppe von Schaltflächen

1. Erstellen Sie ein `ReusableButtons`VSIX-Projekt mit dem Namen . Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehlselementvorlage mit dem Namen **ReusableCommand**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C-Extensibility,** > **Extensibility** und wählen Sie **Benutzerdefinierter Befehl aus.** Ändern Sie im Feld **Name** am unteren Rand des Fensters den Befehlsdateinamen in *ReusableCommand.cs*.

3. Wechseln Sie in der *Datei .vsct* zum Abschnitt Symbole, und suchen Sie das GuidSymbol-Element, das Gruppen und Befehle für das Projekt enthält. Es sollte guidReusableCommandPackageCmdSet heißen.

4. Fügen Sie für jede Schaltfläche, die Sie der Gruppe hinzufügen, ein IDSymbol hinzu, wie im folgenden Beispiel.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Standardmäßig erstellt die Befehlselementvorlage eine Gruppe mit dem Namen **MyMenuGroup** und eine Schaltfläche mit dem von Ihnen angegebenen Namen sowie einen IDSymbol-Eintrag für jeden.

5. Erstellen Sie im Abschnitt Gruppen ein Gruppenelement, das dieselben GUID- und ID-Attribute aufweist wie die im Abschnitt Symbole angegebenen Attribute. Sie können auch eine vorhandene Gruppe oder den Eintrag verwenden, der von der Befehlsvorlage bereitgestellt wird, wie im folgenden Beispiel. Diese Gruppe wird im Menü **Extras** angezeigt.

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>So erstellen Sie eine Gruppe von Schaltflächen zur Wiederverwendung

1. Sie können einen Befehl oder ein Menü in einer Gruppe platzieren, indem Sie die Gruppe entweder als übergeordnete Gruppe in der Definition des Befehls oder Menüs verwenden oder indem Sie den Befehl oder das Menü in der Gruppe mithilfe des Abschnitts CommandPlacements platzieren.

     Definieren Sie im Abschnitt Schaltflächen eine Schaltfläche, die Ihre Gruppe als übergeordnete Schaltfläche enthält, oder verwenden Sie die Schaltfläche, die von der Paketvorlage bereitgestellt wird, wie im folgenden Beispiel gezeigt.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Wenn eine Schaltfläche in mehr als einer Gruppe angezeigt werden muss, erstellen Sie einen Eintrag dafür im Abschnitt CommandPlacements, der nach dem Abschnitt Befehle platziert werden muss. Legen Sie die GUID- und ID-Attribute des CommandPlacement-Elements so fest, dass sie mit denen der Schaltfläche übereinstimmen, die Sie positionieren möchten, und legen Sie dann die GUID und ID des übergeordneten Elements auf die Attribute der Zielgruppe fest, wie im folgenden Beispiel gezeigt.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Der Wert des Feldes Priorität bestimmt die Position des Befehls in der neuen Befehlsgruppe. Im CommandPlacement-Element festgelegte Prioritäten überschreiben die in der Elementdefinition festgelegten Prioritäten. Befehle mit niedrigeren Prioritätswerten werden vor Befehlen mit höheren Prioritätswerten angezeigt. Doppelte Prioritätswerte sind zulässig, aber die relative Position von Befehlen mit demselben Prioritätswert kann nicht garantiert werden, da die Reihenfolge, in der der Befehl **devenv /setup** die endgültige Schnittstelle aus der Registrierung erstellt, möglicherweise nicht konsistent ist.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>So setzen Sie eine wiederverwendbare Gruppe von Schaltflächen in ein Menü

1. Erstellen Sie einen `CommandPlacements` Eintrag im Abschnitt. Legen Sie die GUID `CommandPlacement` und ID des Elements auf die der Gruppe fest, und legen Sie die übergeordnete GUID und ID auf die des Zielspeicherorts fest.

    Der Abschnitt CommandPlacements sollte direkt nach dem Abschnitt Befehle platziert werden:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Eine Befehlsgruppe kann in mehr als einem Menü enthalten sein. Das übergeordnete Menü kann ein menü sein, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] das Sie erstellt haben, eines, das von bereitgestellt wird (wie in *ShellCmdDef.vsct* oder *SharedCmdDef.vsct*beschrieben), oder eines, das in einem anderen VSPackage definiert ist. Die Anzahl der übergeordneten Layer ist unbegrenzt, solange [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] das übergeordnete Menü schließlich mit oder mit einem Kontextmenü verbunden ist, das von einem VSPackage angezeigt wird.

    Im folgenden Beispiel wird die Gruppe auf der Symbolleiste des **Projektmappen-Explorers** rechts neben den anderen Schaltflächen angezeigt.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
