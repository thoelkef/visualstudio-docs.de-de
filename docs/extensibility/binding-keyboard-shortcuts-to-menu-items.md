---
title: Binden von Tastaturverknüpfungen an Menüelemente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740025"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Binden von Tastenkombinationen an Menüelemente
Um eine Tastenkombination an einen benutzerdefinierten Menübefehl zu binden, fügen Sie einfach einen Eintrag zur *.vsct-Datei* für das Paket hinzu. In diesem Thema wird erläutert, wie Sie eine Tastenkombination einer benutzerdefinierten Schaltfläche, einem Menüelement oder einem Symbolleistenbefehl zuordnen und wie Sie die Tastaturzuordnung im Standardeditor anwenden oder auf einen benutzerdefinierten Editor beschränken.

 Informationen zum Zuweisen von Tastenkombinationen zu vorhandenen Visual Studio-Menüelementen finden Sie unter Identifizieren und Anpassen von [Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Wählen Sie eine Tastenkombination
 Viele Tastenkombinationen werden bereits in Visual Studio verwendet. Sie sollten nicht dieselbe Verknüpfung mehreren Befehlen zuweisen, da doppelte Bindungen schwer zu erkennen sind und auch zu unvorhersehbaren Ergebnissen führen können. Daher ist es eine gute Idee, die Verfügbarkeit einer Verknüpfung zu überprüfen, bevor Sie sie zuweisen.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>So überprüfen Sie die Verfügbarkeit einer Tastenkombination

1. Wählen Sie im Fenster **Keyboard** **Werkzeugoptionen** > **Options** > **Umgebung** Tastatur aus.

2. Stellen Sie sicher, dass **Die Verwendung neuer Verknüpfungen in** auf **Global**festgelegt ist.

3. Geben Sie im Feld **Tastenkombination drücken** die Tastenkombination ein, die Sie verwenden möchten.

    Wenn die Verknüpfung bereits in Visual Studio verwendet wird, wird im Feld **Shortcut,** das derzeit von verwendet wird, der Befehl angezeigt, den die Verknüpfung derzeit aufruft.

4. Probieren Sie verschiedene Tastenkombinationen aus, bis Sie eine schlüsselweise gefunden haben, die nicht zugeordnet ist.

   > [!NOTE]
   > Tastenkombinationen, die **Alt** verwenden, können ein Menü öffnen und nicht direkt einen Befehl ausführen. Daher ist das Feld Shortcut, das **derzeit von verwendet wird,** möglicherweise leer, wenn Sie eine Verknüpfung eingeben, die **Alt**enthält. Sie können überprüfen, ob die Verknüpfung kein Menü öffnet, indem Sie das Dialogfeld **Optionen** schließen und dann die Tasten drücken.

   Im folgenden Verfahren wird davon ausgegangen, dass Sie über ein vorhandenes VSPackage mit einem Menübefehl verfügen. Wenn Sie Hilfe benötigen, werfen Sie einen Blick auf [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>So weisen Sie einem Befehl eine Tastenkombination zu

1. Öffnen Sie die *.vsct-Datei* für Ihr Paket.

2. Erstellen Sie `<KeyBindings>` einen `<Commands>` leeren Abschnitt nach dem, wenn er nicht bereits vorhanden ist.

   > [!WARNING]
   > Weitere Informationen zu Schlüsselbindungen finden Sie unter [Schlüsselbindung](../extensibility/keybinding-element.md).

    Erstellen `<KeyBindings>` Sie im `<KeyBinding>` Abschnitt einen Eintrag.

    Legen `guid` Sie `id` die Und-Attribute auf die Attribute des Befehls fest, den Sie aufrufen möchten.

    Legen `mod1` Sie das Attribut auf **Control**, **Alt**oder **Shift**fest.

    Der Abschnitt KeyBindings sollte etwa wie folgt aussehen:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Wenn Ihre Tastenkombination mehr als zwei `mod2` `key2` Tasten erfordert, legen Sie die und die Attribute fest.

   In den meisten Fällen sollte **Shift** nicht ohne einen zweiten Modifikator verwendet werden, da das Drücken bereits dazu führt, dass die meisten alphanumerischen Schlüssel einen Großbuchstaben oder ein Symbol eingeben.

   Mit Virtual-Key-Codes können Sie auf spezielle Schlüssel zugreifen, denen kein Zeichen zugeordnet ist, z. B. Funktionstasten und die **Backspace-Taste.** Weitere Informationen finden Sie unter [Virtual-Key-Codes](/windows/desktop/inputdev/virtual-key-codes).

   Um den Befehl im Visual Studio-Editor `editor` verfügbar `guidVSStd97`zu machen, legen Sie das Attribut auf fest.

   Um den Befehl nur in einem benutzerdefinierten Editor verfügbar zu machen, legen Sie das `editor` Attribut auf den Namen des benutzerdefinierten Editors fest, der von der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paketvorlage generiert wurde, als Sie das VSPackage erstellt haben, das den benutzerdefinierten Editor enthält. Um den Namenswert zu `<Symbols>` finden, `<GuidSymbol>` suchen `name` Sie im`editorfactory`Abschnitt nach einem Knoten, dessen Attribut auf "." endet. Dies ist der Name des benutzerdefinierten Editors.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die Tastenkombination **Strg**+**Alt**+**C** an einen Befehl mit dem `cmdidMyCommand` `MyPackage`Namen "" gebunden.

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die Tastenkombination **Strg**+**B** an einen Befehl mit dem Namen `cmdidBold` in einem Projekt mit dem Namen `TestEditor`gebunden. Der Befehl ist nur im benutzerdefinierten Editor und nicht in anderen Editoren verfügbar.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
