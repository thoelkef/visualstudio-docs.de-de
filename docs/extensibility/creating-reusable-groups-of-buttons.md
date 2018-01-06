---
title: "Erstellen von Wiederverwendbaren Gruppen von Schaltflächen mit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: "44"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c2ac175d2fd267500f19e9f22cd46d88dcc9f314
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-reusable-groups-of-buttons"></a>Erstellen von Wiederverwendbaren Gruppen von Schaltflächen
Eine Befehlsgruppe ist eine Auflistung von Befehlen, die immer zusammen in einem Menü oder die Symbolleiste angezeigt werden. Alle Befehlsgruppe kann erneut verwendet werden, indem anderen übergeordneten Menüs im Abschnitt CommandPlacements der VSCT-Datei zuweisen.  
  
 Befehlsgruppen Schaltflächen in der Regel enthalten, aber sie können auch andere Menüs oder Kombinationsfelder enthalten.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>So erstellen eine wieder verwendbare Gruppe von Schaltflächen  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `ReusableButtons`. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage für benutzerdefinierte Befehl mit dem Namen **ReusableCommand**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Befehl**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **ReusableCommand.cs**.  
  
3.  Finden Sie in der VSCT-Datei im Abschnitt Symbole, und suchen Sie das GuidSymbol-Element, das Gruppen und Befehle für das Projekt enthält. Es sollten GuidReusableCommandPackageCmdSet benannt werden.  
  
4.  Fügen Sie eine IDSymbol für jede Schaltfläche, mit denen Sie die Gruppe an, wie im folgenden Beispiel hinzugefügt werden.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Standardmäßig wird die Elementvorlage für den Befehl erstellt eine Gruppe namens **"MyGroup"** und eine Schaltfläche mit dem Namen, den Sie angegeben haben, zusammen mit einer IDSymbol-Eintrag für jede.  
  
5.  Erstellen Sie im Abschnitt Gruppen ein Group-Element, das die gleichen GUID und ID-Attribute als diejenigen, die im Abschnitt Symbole angegeben wurde. Sie können eine vorhandene Gruppe verwenden, oder verwenden den Eintrag, der von der-Befehlsvorlage, wie im folgenden Beispiel bereitgestellt wird. Diese Gruppe wird angezeigt, auf die **Tools** Menü  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>So erstellen eine Gruppe von Schaltflächen zur Wiederverwendung  
  
1.  Sie können einen Befehl oder ein Menü in einer Gruppe mithilfe der Gruppe als übergeordnetes Element in der Definition der Befehl oder im Menü oder indem Sie den Befehl oder im Menü in der Gruppe mithilfe des Abschnitts CommandPlacements einfügen einfügen.  
  
     Klicken Sie im Abschnitt Schaltflächen definieren Sie eine Schaltfläche, die Ihre Gruppe wie das übergeordnete Objekt hat, oder verwenden Sie die Schaltfläche, die durch die Paketvorlage bereitgestellt wird, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Wenn Sie eine Schaltfläche in mehr als einer Gruppe angezeigt werden muss, erstellen Sie einen Eintrag für sie im Abschnitt CommandPlacements, die nach dem Abschnitt Befehle platziert werden muss. Legen Sie die GUID und ID-Attribute des Elements CommandPlacement auf die Schaltfläche "" übereinstimmen, die Sie positionieren möchten, und legen Sie dann die GUID und die ID des übergeordneten Elements mit denen der Zielgruppe, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Der Wert des Felds Priorität bestimmt die Position des Befehls in die neue Befehlsgruppe. Legen Sie Prioritäten in der CommandPlacement Element zu überschreiben, die in der Elementdefinition. Befehle, die niedrigere Prioritätswerte haben, werden vor Befehlen angezeigt, die höhere Prioritätswerte haben. Doppelte Prioritätswerte sind zulässig, aber die relativen Positionen von Befehlen, die den gleichen Prioritätswert aufweisen kann nicht garantiert werden, da die Reihenfolge, in der die **Devenv/Setup** Befehl wird die endgültige Benutzeroberfläche aus der Registrierung erstellt. möglicherweise nicht konsistent sein.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Eine wiederverwendbare Gruppe von Schaltflächen in einem Menü eingefügt werden soll.  
  
1.  Erstellen Sie einen Eintrag in der `CommandPlacements` Abschnitt. Legen Sie die GUID und die ID des der `CommandPlacement` Element, mit denen der Gruppe, und legen Sie das übergeordnete Element GUID und ID auf die von den Zielspeicherort an.  
  
     Abschnitt CommandPlacements sollte nur nach dem Abschnitt Befehle:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Eine Befehlsgruppe kann mehr als ein Menü eingefügt werden. Im übergeordneten Menü möglich, die Sie erstellt haben, eine, die vom bereitgestellte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (wie in beschrieben ShellCmdDef.vsct oder SharedCmdDef.vsct), oder, wenn in einem anderen VSPackage definiert ist. Die Anzahl der Ebenen Überordnung ist unbegrenzt, als im übergeordneten Menü letztendlich verbunden ist [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder um ein Kontextmenü aufrufen, die durch ein VSPackage angezeigt wird.  
  
     Im folgende Beispiel wird die Gruppe der **Projektmappen-Explorer** Symbolleiste rechts neben die anderen Schaltflächen.  
  
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