---
title: Erstellen einer benutzerdefinierten Startseite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71892262d98b175b111218068a02d03ad3d04caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100682"
---
# <a name="creating-a-custom-start-page"></a>Erstellen einer benutzerdefinierten Startseite
Sie können eine benutzerdefinierte Startseite erstellen, anhand der Schritte in diesem Dokument.  
  
## <a name="creating-a-blank-start-page"></a>Erstellen einer leeren Startseite  
 Stellen Sie zunächst eine leere Startseite erstellen Sie eine XAML-Datei mit einem Tag-Struktur, die Visual Studio erkennt. Anschließend fügen Sie Markup und CodeBehind erzeugt das Aussehen und die gewünschten Funktionen.  
  
#### <a name="to-create-a-blank-start-page"></a>Eine leere Startseite erstellen  
  
1.  Erstellen eines neuen Projekts vom Typ **WPF-Anwendung** (**Visual c# / Windows-Desktop**.  
  
2.  Fügen Sie einen Verweis auf `Microsoft.VisualStudio.Shell.14.0` hinzu.  
  
3.  Die XAML-Datei im XML-Editor öffnen und Ändern der obersten Ebene \<Fenster >-Elements auf eine \<UserControl >-Element ohne Entfernen Sie die Namespacedeklarationen.  
  
4.  Entfernen Sie die `x:Class` Deklaration von Element der obersten Ebene. Dadurch wird die Verwendung von XAML-Inhalt kompatibel mit dem Visual Studio-Toolfenster, das die Startseite hostet.  
  
5.  Fügen Sie die folgenden Namespacedeklarationen hinzu, auf der obersten Ebene \<UserControl > Element.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Diese Namespaces können Sie die Visual Studio-Befehle, Steuerelemente und UI-Einstellungen zugreifen. Weitere Informationen finden Sie unter [Hinzufügen von Visual Studio-Befehle auf einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Das folgende Beispiel zeigt das Markup in der XAML-Datei für eine leere Startseite. Alle benutzerdefinierter Inhalt in der inneren verwendende <xref:System.Windows.Controls.Grid> Element.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Hinzufügen von Steuerelementen zu den leeren \<UserControl >-Elements auf die benutzerdefinierte Startseite ausfüllen. Informationen zum Hinzufügen von Funktionen, die für Visual Studio spezifisch sind, finden Sie unter [Hinzufügen von Visual Studio-Befehle auf einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testen und Anwenden der benutzerdefinierten Startseite  
 Legen Sie die primäre Instanz von Visual Studio der benutzerdefinierten Startseite ausgeführt werden soll, bis Sie sicherstellen, dass Visual Studio kein Absturz erfolgt nicht. Testen Sie es stattdessen in der experimentellen Instanz ein.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>So testen Sie eine manuell erstellte benutzerdefinierte Startseite  
  
1.  Kopieren der XAML-Datei, und alle unterstützenden Textdateien oder Markup, zu der **%USERPROFILE%\My Dateien\Visual Studio 2015\StartPages\\**  Ordner.  
  
2.  Wenn Ihre Startseite verweist auf keine Steuerelemente oder die Typen in Assemblys, die von Visual Studio nicht installiert sind, kopieren Sie die Assemblys, und fügen Sie sie in * Visual Studio-Installation Ordner ***\Common7\IDE\PrivateAssemblies\\** .  
  
3.  Geben Sie an einer Visual Studio-Eingabeaufforderung **Devenv /rootsuffix Exp** eine experimentelle Instanz von Visual Studio zu öffnen.  
  
4.  Wechseln Sie in der experimentellen Instanz zu den **Extras / Optionen / Umgebung / Start** Seite und wählen Sie die XAML-Datei aus der **Startseite anpassen** Dropdownliste.  
  
5.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
     Ihre benutzerdefinierte Startseite angezeigt werden sollen. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, nehmen Änderungen vor kopieren und fügen Sie die geänderten Dateien und öffnen Sie dann erneut die experimentelle Instanz um die Änderungen anzuzeigen.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Zum Anwenden der benutzerdefinierten Startseite in der primären Instanz von Visual Studio  
  
-   Nachdem Sie Ihre Startseite getestet und stabil sein gefunden haben, verwenden die **Startseite anpassen** option die **Optionen** (Dialogfeld), um sie als Startseite in der primären Instanz von Visual Studio auszuwählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML an die Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Hinzufügen des Benutzersteuerelements an die Startseite](../extensibility/adding-user-control-to-the-start-page.md)   
 [Hinzufügen von Visual Studio-Befehle auf einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Bereitstellen von benutzerdefinierten Startseiten](../extensibility/deploying-custom-start-pages.md)