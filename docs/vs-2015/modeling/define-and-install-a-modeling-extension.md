---
title: Definieren und installieren eine modellierungserweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6f7895916cc4ee877c53b056f703d8e46b64b409
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805566"
---
# <a name="define-and-install-a-modeling-extension"></a>Definieren und Installieren einer Modellierungserweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie Erweiterungen zum Modellieren von Diagrammen definieren. Auf diese Weise können Sie die Diagramme und Modelle Ihren eigenen Anforderungen anpassen. Sie können z. B. Menübefehle, UML-Profile, Validierungseinschränkungen und Toolboxelemente definieren. In einer Erweiterung können mehrere Komponenten definiert werden. Sie können diese Erweiterungen auch anderen Visual Studio-Benutzern in Form einer [Visual Studio Integration Extension (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780)bereitstellen. Eine VSIX können Sie mithilfe eines VSIX-Projekts in Visual Studio erstellen.  
  
## <a name="requirements"></a>Anforderungen  
 Siehe [Anforderungen](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-modeling-extension-solution"></a>Erstellen einer Modellierungserweiterungs-Projektmappe  
 Zum Definieren einer Modellierungserweiterung müssen Sie eine Projektmappe erstellen, die die folgenden Projekte enthält:  
  
- Ein VSIX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integration Extension)-Projekt. Dadurch wird eine Datei generiert, die als Installationsprogramm für die Komponenten der Erweiterung fungiert.  
  
- Ein Klassenbibliotheksprojekt, das für Komponenten benötigt wird, die Programmcode enthalten.  
  
  Wenn Sie eine Erweiterung mit mehreren Komponenten erstellen möchten, können Sie diese in einer einzigen Projektmappe entwickeln. Sie benötigen lediglich ein VSIX-Projekt.  
  
  Komponenten, für die kein Code erforderlich ist (beispielsweise benutzerdefinierte Toolboxelemente und benutzerdefinierte UML-Profile) können dem VSIX-Projekt direkt hinzugefügt werden, ohne dass separate Klassenbibliothekprojekte benötigt werden. Komponenten, für die Programmcode erforderlich ist, können viel leichter in einem separaten Klassenbibliothekprojekt definiert werden. Komponenten, die Code wie beispielsweise Gestenhandler, Menübefehle oder Überprüfungscode benötigen.  
  
#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Erstellen eines Klassenbibliothekprojekts für Menübefehle, Gestenhandler oder Überprüfung  
  
1.  Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Projekt**aus.  
  
2.  Wählen Sie unter **Installierte Vorlagen**die Option **Visual C#** oder **Visual Basic**aus, und wählen Sie anschließend **Klassenbibliothek**aus.  
  
#### <a name="to-create-a-vsix-project"></a>So erstellen Sie ein VSIX-Projekt  
  
1.  Wenn Sie eine Komponente mit Code erstellen, ist es am einfachsten, zuerst das Klassenbibliotheksprojekt zu erstellen. Diesem Projekt wird der Code hinzugefügt.  
  
2.  Erstellen eines VSIX-Projekts  
  
    1.  Wählen Sie im **Projektmappen-Explorer**im Kontextmenü der Projektmappe die Option **Hinzufügen**und dann **Neues Projekt**aus.  
  
    2.  Erweitern Sie unter **Installierte Vorlagen**den Knoten **Visual C#** oder **Visual Basic**, und wählen Sie anschließend **Erweiterungen**aus. Wählen Sie in der mittleren Spalte **VSIX Project**.  
  
3.  Legen Sie das VSIX-Projekt als Startprojekt der Projektmappe fest.  
  
    -   Wählen Sie im Projektmappen-Explorer im Kontextmenü des VSIX-Projekts die Option **Als Startprojekt festlegen**aus.  
  
4.  Öffnen Sie **source.extension.vsixmanifest**. Die Datei wird im Manifest-Editor geöffnet.  
  
5.  Legen Sie auf der Registerkarte **MetaData** den Namen und die Beschreibungsfelder des VSIX fest.  
  
6.  Klicken Sie auf der Registerkarte **Ziele installieren** auf **Neu** , und legen Sie dann die Visual Studio-Versionen als Ziele fest.  
  
7.  Fügen Sie Ihre Komponenten auf der Registerkarte **Objekte** der Visual Studio-Erweiterung hinzu.  
  
    1.  Wählen Sie **Neu**aus.  
  
    2.  Legen Sie diese Felder für eine Komponente mit Code im Dialogfeld **Neues Objekt hinzufügen** fest:  
  
        |||  
        |-|-|  
        |**Typ** =|**Microsoft.VisualStudio.MefComponent**|  
        |**Source** =|**Ein Projekt in der aktuellen Projektmappe**|  
        |**Projekt** =|*Ihr Klassenbibliotheksprojekt*|  
        |**Betten in diesen Ordner ein** =|*(leer)*|  
  
         Informationen zu anderen Komponententypen finden Sie unter den Links im nächsten Abschnitt.  
  
## <a name="developing-the-component"></a>Entwickeln der Komponente  
 Sie müssen für jede Komponente (z. B. für einen Menübefehl oder Gestenhandler) einen separaten Handler definieren. Sie können mehrere Handler in das gleiche Klassenbibliotheksprojekt einfügen. In der folgenden Tabelle erhalten Sie eine Übersicht über die verschiedenen Arten von Handlern.  
  
|Erweiterungstyp|Thema|Typische Deklaration der einzelnen Komponenten|  
|--------------------|-----------|----------------------------------------------|  
|Menübefehl|[Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|  
|Drag & Drop oder Doppelklick|[Definieren eines Gestenhandlers in einem Modellierungsdiagramm](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|  
|Validierungseinschränkung|[Definieren von Validierungseinschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|  
|Arbeitsaufgabenlink-Ereignishandler|[Definieren eines Linkhandlers für Arbeitselemente](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|  
|UML-Profil|[Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md)|(Muss definiert werden)|  
|Toolboxelement|[Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox](../modeling/define-a-custom-modeling-toolbox-item.md)|(Muss definiert werden)|  
  
## <a name="running-an-extension-during-its-development"></a>Ausführen einer Erweiterung während ihrer Entwicklung  
  
#### <a name="to-run-an-extension-during-its-development"></a>So führen Sie eine Erweiterung während ihrer Entwicklung aus  
  
1.  Wählen Sie im Menü [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **Debuggen** das Element **Start Debuggenging**aus.  
  
     Das Projekt wird erstellt, und eine neue Instanz von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] wird im Testmodus gestartet.  
  
    -   Alternativ können Sie auch **Starten ohne Debugging**auswählen. Dadurch wird das Programm schneller gestartet.  
  
2.  Erstellen oder öffnen Sie in der experimentellen Instanz von Visual Studio ein Modellierungsprojekt, und erstellen oder öffnen Sie ein Diagramm.  
  
     Die Erweiterung wird geladen und ausgeführt.  
  
3.  Wenn Sie **Starten ohne Debugging** ausgewählt haben, den Debugger aber verwenden möchten, wechseln Sie zurück zur Hauptinstanz von Visual Studio. Klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**. Wählen Sie im Dialogfeld die experimentelle Instanz von Visual Studio aus, die den Programmnamen **devenv**hat.  
  
##  <a name="Installing"></a> Installieren und Deinstallieren einer Erweiterung  
 Führen Sie die folgenden Schritte aus, um Ihre Erweiterung in der Hauptinstanz von Visual Studio auszuführen, entweder auf dem eigenen Computer oder auf anderen Computern.  
  
1.  Suchen Sie auf dem Computer nach der **.vsix** -Datei, die vom Erweiterungsprojekt erstellt wurde.  
  
    1.  Wählen Sie im **Projektmappen-Explorer**im Kontextmenü Ihres Projekts **Ordner in Windows Explorer öffnen**aus.  
  
    2.  Suchen Sie die Datei **Bin\\\*\\**_IhrProjekt_**VSIX**  
  
2.  Kopieren Sie die **.vsix** -Datei auf den Zielcomputer, auf dem Sie die Erweiterung installieren möchten. Dies kann Ihr eigener Computer oder ein anderer Computer sein.  
  
    -   Der Zielcomputer muss über eine der Editionen von Visual Studio verfügen, die Sie auf der Registerkarte **Installationsziele** von **source.extension.vsixmanifest**angegeben haben.  
  
3.  Öffnen Sie auf dem Zielcomputer die Datei **.vsix** , indem Sie beispielsweise darauf doppelklicken.  
  
     **Installer für Visual Studio-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.  
  
4.  Starten Sie Visual Studio.  
  
#### <a name="to-uninstall-an-extension"></a>So deinstallieren Sie eine Erweiterung  
  
1. Klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**.  
  
2. Erweitern Sie **Installierte Erweiterungen**.  
  
3. Wählen Sie die Erweiterung aus, und klicken Sie dann auf **Deinstallieren**.  
  
   In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs-Manager keine Informationen angezeigt werden. In diesem Fall können Sie die Erweiterung entfernen, durch das Löschen der Datei von folgendem Speicherort, in denen *%LocalAppData%* ist in der Regel *DriveName*: \Users\\*Benutzername*\AppData\Local:  
  
   *%LocalAppData%* **\Microsoft\VisualStudio\\[Version] \Extensions**  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definieren von validierungseinschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md)   
 [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)



