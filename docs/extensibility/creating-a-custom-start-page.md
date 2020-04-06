---
title: Erstellen einer benutzerdefinierten Startseite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739631"
---
# <a name="creating-a-custom-start-page"></a>Erstellen einer benutzerdefinierten Startseite

Sie können eine benutzerdefinierte Startseite erstellen, indem Sie die Schritte in diesem Dokument ausführen.

## <a name="create-a-blank-start-page"></a>Erstellen einer leeren Startseite

Erstellen Sie zunächst eine leere Startseite, indem Sie eine *Xaml-Datei* mit einer Tagstruktur erstellen, die Visual Studio erkennt. Fügen Sie dann Markup und CodeBehind hinzu, um die gewünschte Darstellung und Funktionalität zu erzeugen.

1. Erstellen Sie ein neues Projekt vom Typ **WPF-Anwendung** (**Visual C-Windows** > **Desktop**).

2. Fügen Sie einen Verweis auf `Microsoft.VisualStudio.Shell.14.0` hinzu.

3. Öffnen Sie die XAML-Datei im XML-Editor, und ändern Sie das Fenster->-Element der obersten Ebene \<in ein \<UserControl->-Element, ohne die Namespacedeklarationen zu entfernen.

4. Entfernen `x:Class` Sie die Deklaration aus dem Element der obersten Ebene. Dadurch ist der XAML-Inhalt mit dem Visual Studio-Toolfenster kompatibel, in dem die Startseite gehostet wird.

5. Fügen Sie die folgenden Namespacedeklarationen zum>-Element der obersten Ebene \<hinzu.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Mit diesen Namespaces können Sie auf Visual Studio-Befehle, Steuerelemente und UI-Einstellungen zugreifen. Weitere Informationen finden Sie unter Hinzufügen von [Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Das folgende Beispiel zeigt das Markup in der *.xaml-Datei* für eine leere Startseite. Jeder benutzerdefinierte Inhalt sollte <xref:System.Windows.Controls.Grid> in das innere Element eingehen.

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

6. Fügen Sie dem \<leeren UserControl->-Element Steuerelemente hinzu, um Ihre benutzerdefinierte Startseite auszufüllen. Informationen zum Hinzufügen von Funktionen, die für Visual Studio spezifisch sind, finden Sie unter Hinzufügen von [Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Testen und Anwenden der benutzerdefinierten Startseite

Legen Sie die primäre Instanz von Visual Studio erst so fest, dass die benutzerdefinierte Startseite ausgeführt wird, wenn Sie überprüfen, dass Visual Studio nicht abstürzt. Testen Sie es stattdessen in der experimentellen Instanz.

### <a name="to-test-a-manually-created-custom-start-page"></a>So testen Sie eine manuell erstellte benutzerdefinierte Startseite

1. Kopieren Sie Ihre XAML-Datei und alle unterstützenden Textdateien oder Markupdateien in den Ordner *%USERPROFILE%-Meine Dokumente, Visual Studio 2015, StartPages.\\ *

2. Wenn Ihre Startseite auf Steuerelemente oder Typen in Assemblys verweist, die nicht von Visual Studio installiert sind, kopieren Sie die Assemblys, und fügen Sie sie dann in den *Installationsordner "Visual\\Studio"* ein.

3. Geben Sie an einer Visual Studio-Eingabeaufforderung **devenv /rootsuffix Exp** ein, um eine experimentelle Instanz von Visual Studio zu öffnen.

4. Wechseln Sie in der **Tools** > experimentellen Instanz zur Seite "Tools**Options** > **Environment** > **Startup"** und wählen Sie Ihre XAML-Datei aus der Dropdown-Liste Startseite **anpassen** aus.

5. Klicken Sie im Menü **Ansicht** auf **Startseite**.

     Ihre benutzerdefinierte Startseite sollte angezeigt werden. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, die Änderungen vornehmen, die geänderten Dateien kopieren und einfügen und dann die experimentelle Instanz erneut öffnen, um die Änderungen anzuzeigen.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>So wenden Sie die benutzerdefinierte Startseite in der primären Instanz von Visual Studio an

- Nachdem Sie Ihre Startseite getestet und als stabil befunden haben, verwenden Sie die Option **Startseite anpassen** im Dialogfeld **Optionen,** um sie als Startseite in der primären Instanz von Visual Studio auszuwählen.

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Hinzufügen von Benutzersteuerelementen zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)
- [Hinzufügen von Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Bereitstellen benutzerdefinierter Startseiten](../extensibility/deploying-custom-start-pages.md)
