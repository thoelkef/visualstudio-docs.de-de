---
title: Binden von Tastenkombinationen an Menüelemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f661129a4706ce0ac501a5fbad9a7ce5a60e3127
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514972"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Binden von Tastenkombinationen an Menüelemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Binden von Tastenkombinationen an Menüelemente](https://docs.microsoft.com/visualstudio/extensibility/binding-keyboard-shortcuts-to-menu-items).  
  
Um eine Tastenkombination an einen benutzerdefinierten Befehl zu binden, fügen Sie nur einen Eintrag in die VSCT-Datei für das Paket. In diesem Thema wird erläutert, wie eine benutzerdefinierte Schaltfläche, Menüelement oder Befehle der Hilfesymbolleiste eine Tastenkombination zugeordnet, und das Anwenden der Zuordnung von Tastenkombinationen in der Standard-Editor oder nur für einen benutzerdefinierten Editor.  
  
 Um vorhandene Visual Studio-Menüelemente Tastenkombinationen zuweisen möchten, finden Sie unter [identifizieren und Anpassen von Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Wählen eine Tastenkombination  
 Viele Tastenkombinationen sind bereits in Visual Studio verwendet. Sie sollten nicht das gleiche abgekürzte Verfahren für mehr als einen Befehl zuweisen, da doppelte Bindungen schwer sind zu erkennen, und können ebenfalls zu unvorhersehbaren Ergebnissen führen. Aus diesem Grund ist es eine gute Idee, überprüfen die Verfügbarkeit einer Tastenkombination ein, bevor Sie sie zuweisen.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Um zu überprüfen, ob die Verfügbarkeit einer Tastenkombination  
  
1.  In der **Extras / Optionen / Umgebung** wählen Sie im Fenster **Tastatur**.  
  
2.  Stellen Sie sicher, dass **verwenden neue Verknüpfung in** nastaven NA hodnotu **Global**.  
  
3.  In der **Tastenkombination drücken** geben die Tastenkombination, die Sie verwenden möchten.  
  
     Wenn die Verknüpfung bereits in Visual Studio verwendet wird die **Sicherheitsrolle, die momentan verwendet von** Feld wird den Befehl, der derzeit, die Verknüpfung aufruft angezeigt.  
  
4.  Versuchen Sie es für verschiedene Kombinationen von Schlüsseln aus, bis Sie einen finden, die nicht zugeordnet ist.  
  
    > [!NOTE]
    >  Tastenkombinationen in Visual Studio, die ALT-Taste verwenden möglicherweise ein Menü öffnen und nicht direkt einen Befehl ausführen. Aus diesem Grund die **Sicherheitsrolle, die momentan verwendet von** Feld möglicherweise leer, wenn Sie eine Verknüpfung eingeben, die ALT-Taste enthält. Sie können überprüfen, ob die Verknüpfung ein Menüs nicht durch Schließen geöffnet wird die **Optionen** (Dialogfeld), und drücken die Schlüssel.  
  
 Das folgende Verfahren wird davon ausgegangen, dass Sie einen vorhandenen VSPackage mit einem Menübefehl verfügen. Wenn Sie hierzu Hilfe benötigen, sehen Sie sich [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Ein Befehl eine Tastenkombination zuweisen  
  
1.  Öffnen Sie die VSCT-Datei für Ihr Paket.  
  
2.  Erstellen Sie eine leere `<KeyBindings>` -Abschnitt nach dem `<Commands>` ist dies nicht bereits vorhanden.  
  
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
  
 Virtuelle Tastencodes können Sie die spezielle Schlüssel zugreifen, die nicht mit einem Zeichen zugeordnet sind, z. B. Funktionstasten verfügen und die **RÜCKTASTE** Schlüssel. Weitere Informationen finden Sie unter [virtuelle Tastencodes](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Der Befehl zur Verfügung, in der Visual Studio-Editor-legen fest, um die `editor` Attribut `guidVSStd97`.  
  
 Um den Befehl nur in einen benutzerdefinierten Editor verfügbar machen, legen die `editor` -Attribut auf den Namen des benutzerdefinierten Editors, die vom generiert wurde, die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Paket-Vorlage, wenn Sie das VSPackage erstellt, enthält den benutzerdefinierten Editor. Um die Name-Wert zu suchen, suchen Sie in der `<Symbols>` im Abschnitt für eine `<GuidSymbol>` Knoten, deren `name` Attribut endet, in "`editorfactory`." Dies ist der Name des benutzerdefinierten Editors.  
  
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
 In diesem Beispiel bindet die Tastenkombination STRG + B, um einen Befehl mit dem Namen `cmdidBold` in einem Projekt namens `TestEditor`. Der Befehl ist nur in den benutzerdefinierten Editor und nicht in anderen Editoren verfügbar.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)

