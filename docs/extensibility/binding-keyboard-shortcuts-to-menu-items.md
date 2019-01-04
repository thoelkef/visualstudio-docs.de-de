---
title: Binden von Tastenkombinationen an Menüelemente | Microsoft-Dokumentation
ms.date: 11/04/2016
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
ms.openlocfilehash: d319dfdf1203870ecc1b80787522a56d6f37b5e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940374"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Binden von Tastenkombinationen an Menüelemente
Um eine Tastenkombination an einen benutzerdefinierten Befehl zu binden, nur einen Eintrag hinzufügen die *VSCT* Datei für das Paket. In diesem Thema wird erläutert, wie eine benutzerdefinierte Schaltfläche, Menüelement oder Befehle der Hilfesymbolleiste eine Tastenkombination zugeordnet, und das Anwenden der Zuordnung von Tastenkombinationen in der Standard-Editor oder nur für einen benutzerdefinierten Editor.  
  
 Um vorhandene Visual Studio-Menüelemente Tastenkombinationen zuweisen möchten, finden Sie unter [identifizieren und Anpassen von Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choose-a-key-combination"></a>Wählen Sie eine Tastenkombination  
 Viele Tastenkombinationen sind bereits in Visual Studio verwendet. Sie sollten nicht das gleiche abgekürzte Verfahren für mehr als einen Befehl zuweisen, da doppelte Bindungen schwer sind zu erkennen, und können ebenfalls zu unvorhersehbaren Ergebnissen führen. Aus diesem Grund ist es eine gute Idee, überprüfen die Verfügbarkeit einer Tastenkombination ein, bevor Sie sie zuweisen.  
  
### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Um zu überprüfen, ob die Verfügbarkeit einer Tastenkombination  
  
1. In der **Tools** > **Optionen** > **Umgebung** wählen Sie im Fenster **Tastatur**.  
  
2. Stellen Sie sicher, dass **verwenden neue Verknüpfung in** nastaven NA hodnotu **Global**.  
  
3. In der **Tastenkombination drücken** geben die Tastenkombination, die Sie verwenden möchten.  
  
    Wenn die Verknüpfung bereits in Visual Studio verwendet wird die **momentan verwendet von** Feld wird den Befehl, der derzeit, die Verknüpfung aufruft angezeigt.  
  
4. Versuchen Sie es für verschiedene Kombinationen von Schlüsseln aus, bis Sie einen finden, die nicht zugeordnet ist.  
  
   > [!NOTE]
   >  Tastenkombinationen, mit denen **Alt** ein Menü öffnen und einen Befehl nicht direkt ausführen kann. Aus diesem Grund die **momentan verwendet von** Feld möglicherweise leer, wenn Sie eine Verknüpfung eingeben, die enthält **Alt**. Sie können überprüfen, ob die Verknüpfung ein Menüs nicht durch Schließen geöffnet wird die **Optionen** (Dialogfeld), und drücken die Schlüssel.  
  
   Das folgende Verfahren wird davon ausgegangen, dass Sie einen vorhandenen VSPackage mit einem Menübefehl verfügen. Wenn Sie hierzu Hilfe benötigen, sehen Sie sich [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Ein Befehl eine Tastenkombination zuweisen  
  
1. Öffnen der *VSCT* -Datei für Ihr Paket.  
  
2. Erstellen Sie eine leere `<KeyBindings>` -Abschnitt nach dem `<Commands>` ist dies nicht bereits vorhanden.  
  
   > [!WARNING]
   >  Weitere Informationen zu Tastenkombinationen finden Sie unter [Keybinding](../extensibility/keybinding-element.md).  
  
    In der `<KeyBindings>` Abschnitt, erstellen Sie eine `<KeyBinding>` Eintrag.  
  
    Legen Sie die `guid` und `id` Attribute, mit denen des Befehls, die Sie aufrufen möchten.  
  
    Legen Sie die `mod1` Attribut **Steuerelement**, **Alt**, oder **UMSCHALT**.  
  
    Abschnitt KeyBindings sollte etwa wie folgt aussehen:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Wenn Ihre Tastenkombination mehr als zwei Schlüssel erforderlich ist, legen Sie die `mod2` und `key2` Attribute.  
  
   In den meisten Fällen **UMSCHALT** sollte nicht ohne einen zweiten Modifizierer verwendet werden, da es bereits drücken führt dazu, dass die meisten alphanumerische Schlüssel keine Großbuchstaben oder ein Symbol, eingeben.  
  
   Virtuelle Tastencodes können Sie die spezielle Schlüssel zugreifen, die nicht mit einem Zeichen zugeordnet sind, z. B. Funktionstasten verfügen und die **RÜCKTASTE** Schlüssel. Weitere Informationen finden Sie unter [virtuelle Tastencodes](https://docs.microsoft.com/windows/desktop/inputdev/virtual-key-codes).  
  
   Der Befehl zur Verfügung, in der Visual Studio-Editor-legen fest, um die `editor` Attribut `guidVSStd97`.  
  
   Um den Befehl nur in einen benutzerdefinierten Editor verfügbar machen, legen die `editor` -Attribut auf den Namen des benutzerdefinierten Editors, die vom generiert wurde, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Paket-Vorlage, wenn Sie das VSPackage erstellt, enthält den benutzerdefinierten Editor. Um die Name-Wert zu suchen, suchen Sie in der `<Symbols>` im Abschnitt für eine `<GuidSymbol>` Knoten, deren `name` Attribut endet, in "`editorfactory`." Dies ist der Name des benutzerdefinierten Editors.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel bindet die Tastenkombination **STRG**+**Alt**+**C** an einen Befehl mit dem Namen `cmdidMyCommand` in einem Paket mit dem Namen `MyPackage`.  
  
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
 In diesem Beispiel bindet die Tastenkombination **STRG**+**B** an einen Befehl mit dem Namen `cmdidBold` in einem Projekt namens `TestEditor`. Der Befehl ist nur in den benutzerdefinierten Editor und nicht in anderen Editoren verfügbar.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)