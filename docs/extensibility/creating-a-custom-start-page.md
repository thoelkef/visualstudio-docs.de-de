---
title: Erstellen einer benutzerdefinierten Startseite | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2b0b8c6fde31f4f4d9573381e511465e60086add
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336678"
---
# <a name="creating-a-custom-start-page"></a>Erstellen einer benutzerdefinierten Startseite

Sie können eine benutzerdefinierte Startseite erstellen, anhand der Schritte in diesem Dokument.

## <a name="create-a-blank-start-page"></a>Erstellen Sie eine leere Startseite

Stellen Sie zunächst eine leere Startseite durch das Erstellen einer *XAML* -Datei mit einem Tag-Struktur, die Visual Studio erkennt. Anschließend fügen Sie Markup und CodeBehind zu erzeugen, die Darstellung und Funktionalität, die Sie möchten.

1. Erstellen eines neuen Projekts vom Typ **WPF-Anwendung** (**Visual C#-**  > **Windows Desktop**).

2. Fügen Sie einen Verweis auf `Microsoft.VisualStudio.Shell.14.0` hinzu.

3. Öffnen Sie die XAML-Datei im XML-Editor, und Ändern der obersten Ebene \<Fenster >-Element ein \<UserControl >-Element ohne die Namespacedeklarationen zu entfernen.

4. Entfernen Sie die `x:Class` Deklaration aus dem Element oberster Ebene. Dadurch wird den XAML-Inhalt mit der Visual Studio-Toolfenster, das die Startseite hostet kompatibel.

5. Fügen Sie die folgenden Namespacedeklarationen der obersten Ebene \<UserControl > Element.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Diese Namespaces können Sie die Visual Studio-Befehle, Steuerelementen und Einstellungen für Benutzeroberfläche zugreifen. Weitere Informationen finden Sie unter [Befehle aus Visual Studio hinzufügen, um eine Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Das folgende Beispiel zeigt das Markup in der *XAML* -Datei für eine leere Startseite. Alle benutzerdefinierter Inhalt gesendet werden sollen, in der inneren <xref:System.Windows.Controls.Grid> Element.

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

6. Hinzufügen von Steuerelementen auf ein leeres \<UserControl >-Element So füllen Sie die benutzerdefinierte Startseite. Weitere Informationen zum Hinzufügen von Funktionen, die in Visual Studio spezifisch sind, finden Sie unter [Befehle aus Visual Studio hinzufügen, um eine Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Testen und Anwenden der benutzerdefinierten Startseite

Legen Sie die primäre Instanz von Visual Studio der benutzerdefinierten Startseite ausgeführt werden soll, bis Sie sicherstellen, dass Visual Studio kein Absturz erfolgt nicht. Testen Sie es stattdessen in der experimentellen Instanz ein.

### <a name="to-test-a-manually-created-custom-start-page"></a>So testen Sie eine manuell erstellte benutzerdefinierte Startseite

1. Kopieren der XAML-Datei und alle unterstützenden Textdateien oder Markup-Dateien, zu der *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\*  Ordner.

2. Wenn Ihre Startseite verweist keine Steuerelemente oder Typen in Assemblys, die von Visual Studio nicht installiert sind, kopieren Sie die Assemblys, und fügen Sie sie in *{Visual Studio-Installationsordner} \Common7\IDE\PrivateAssemblies\\* .

3. Geben Sie an einer Visual Studio-Eingabeaufforderung **Devenv/rootsuffix Exp** um eine experimentelle Instanz von Visual Studio zu öffnen.

4. Wechseln Sie in der experimentellen Instanz zu den **Tools** > **Optionen** > **Umgebung** > **Start** Seite, und wählen Sie die XAML-Datei aus dem **Customize Start Page** Dropdownliste.

5. Klicken Sie im Menü **Ansicht** auf **Startseite**.

     Der benutzerdefinierten Startseite sollte angezeigt werden. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, nehmen Sie die Änderungen, kopieren und fügen Sie die geänderten Dateien und öffnen Sie erneut die experimentelle Instanz um die Änderungen anzuzeigen.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Zum Anwenden die benutzerdefinierten Startseite in der primären Instanz von Visual Studio

- Verwenden, nachdem Sie Ihre Startseite getestet und fand es stabil sein, die **Customize Start Page** option die **Optionen** im Dialogfeld für die Auswahl als Startseite in der primären Instanz von Visual Studio

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML an die Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Die Startseite Benutzersteuerelement hinzufügen](../extensibility/adding-user-control-to-the-start-page.md)
- [Hinzufügen von Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Exemplarische Vorgehensweise: Speichern von benutzereinstellungen auf einer Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Bereitstellen von benutzerdefinierten Startseiten](../extensibility/deploying-custom-start-pages.md)