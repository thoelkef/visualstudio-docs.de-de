---
title: Binden von Tastenkombinationen auf Menüelemente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db02cf763ee4bf171d862129c88687accab00cc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Bindung von Tastenkombinationen auf Menüelemente
Um eine Tastenkombination zu einem benutzerdefinierten Menübefehl zu binden, fügen Sie nur einen Eintrag zur VSCT-Datei für das Paket. In diesem Thema wird erläutert, wie eine benutzerdefinierte Schaltfläche, Menüelement oder Befehle der Hilfesymbolleiste eine Tastenkombination zugeordnet, und wie Sie das Tastaturzuordnungsschema im Standardeditor anwenden oder nur für einen benutzerdefinierten Editor.  
  
 Vorhandene Visual Studio-Menüelemente Tastenkombinationen zuweisen möchten, finden Sie unter [identifizieren und Anpassen von Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Wählen eine Tastenkombination  
 Viele Tastenkombinationen sind in Visual Studio bereits verwendet. Sie sollten mehrere Befehle nicht das gleiche abgekürzte Verfahren zuweisen, da doppelte Bindungen schwer sind zu erkennen und möglicherweise auch zu unvorhersehbaren Ergebnissen führt. Aus diesem Grund ist es ratsam, überprüfen die Verfügbarkeit einer Verknüpfung aus, bevor Sie es zuweisen.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Um die Verfügbarkeit einer Tastenkombination überprüfen  
  
1.  In der **Extras / Optionen / Umgebung** wählen **Tastatur**.  
  
2.  Stellen Sie sicher, dass **Neue Tastenkomb in** festgelegt ist, um **Global**.  
  
3.  In der **Tastenkombination** geben die Tastenkombination, die Sie verwenden möchten.  
  
     Die Verknüpfung, die bereits in Visual Studio verwendet die **Kontextmenü momentan verwendet von** Feld zeigt die Befehle, die die Verknüpfung derzeit aufrufen.  
  
4.  Probieren Sie verschiedene Kombinationen von Schlüsseln, bis Sie eine gefunden, die nicht zugeordnet ist.  
  
    > [!NOTE]
    >  Tastenkombinationen aufgeführt, die ALT-Taste verwenden möglicherweise ein Menü zu öffnen und einen Befehl nicht direkt ausführen. Aus diesem Grund die **Kontextmenü momentan verwendet von** Feld möglicherweise leer, wenn Sie eine Verknüpfung eingeben, die ALT-Taste enthält. Sie können überprüfen, ob die Verknüpfung ein Menüs nicht schließende öffnen lässt die **Optionen** (Dialogfeld), und drücken die Schlüssel.  
  
 Das folgende Verfahren wird davon ausgegangen, dass Sie eine vorhandene VSPackage mit einem Menübefehl verfügen. Wenn Sie auf diese Weise Hilfe benötigen, sehen Sie sich [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Ein Befehl eine Tastenkombination zuweisen  
  
1.  Öffnen Sie die VSCT-Datei für Ihr Paket.  
  
2.  Erstellen Sie eine leere `<KeyBindings>` nach dem Abschnitt der `<Commands>` , wenn er nicht bereits vorhanden ist.  
  
    > [!WARNING]
    >  Weitere Informationen zu tastenbindungen, finden Sie unter [Keybinding](../extensibility/keybinding-element.md).  
  
     In der `<KeyBindings>` Abschnitt, erstellen Sie eine `<KeyBinding>` Eintrag.  
  
     Legen Sie die `guid` und `id` Attribute, mit denen des Befehls, die Sie aufrufen möchten.  
  
     Legen Sie die `mod1` -Attribut **Steuerelement**, **Alt**, oder **UMSCHALT**.  
  
     Der Abschnitt Schlüsselbindungen sollte etwa wie folgt aussehen:  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 Wenn die Tastenkombination mehr als zwei Schlüssel erforderlich ist, legen Sie die `mod2` und `key2` Attribute.  
  
 In den meisten Situationen **UMSCHALT** sollten nicht ohne einen zweiten Modifizierer verwendet werden, da es bereits drücken führt dazu, die meisten alphanumerische Schlüssel dass, ein Großbuchstabe oder ein Symbol einzugeben.  
  
 Virtuelle Tastencodes können Sie die spezielle Schlüssel zugreifen, die nicht mit einem Zeichen zugeordnet werden, z. B. Funktionstasten verfügen und die **RÜCKTASTE** Schlüssel. Weitere Informationen finden Sie unter [virtuellen Tastencodes](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Um den Befehl Editor in Visual Studio verfügbar machen, legen Sie die `editor` -Attribut `guidVSStd97`.  
  
 Um den Befehl nur in einen benutzerdefinierten Editor verfügbar zu machen, legen Sie die `editor` -Attribut auf den Namen des benutzerdefinierten Editors, die von generiert wurde die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Paket-Vorlage, wenn Sie das VSPackage erstellt schließt den benutzerdefinierten Editor. Um die Name-Wert zu finden, suchen Sie in der `<Symbols>` im Abschnitt für eine `<GuidSymbol>` Knoten, deren `name` Attribut endet in "`editorfactory`." Dies ist der Name des benutzerdefinierten Editors.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel bindet die Tastenkombination STRG + ALT + C an einen Befehl mit dem Namen `cmdidMyCommand` in einem Paket mit dem Namen `MyPackage`.  
  
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
 In diesem Beispiel bindet die Tastenkombination STRG + B, um einen Befehl mit dem Namen `cmdidBold` in einem Projekt mit dem Namen `TestEditor`. Der Befehl ist nur in den benutzerdefinierten Editor und nicht in anderen Editoren verfügbar.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)