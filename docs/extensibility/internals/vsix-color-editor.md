---
title: VSIX Farbeditor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704042"
---
# <a name="vsix-color-editor"></a>VSIX-Farb-Editor
Das Visual Studio-Erweiterungsfarbeditor-Tool kann benutzerdefinierte Farben für Visual Studio erstellen und bearbeiten. Das Tool kann auch Designressourcenschlüssel generieren, sodass die Farben im Code verwendet werden können. Dieses Tool ist nützlich zum Erstellen von Farben für eine Visual Studio-Erweiterung, die Dies unterstützt. Dieses Tool kann .pkgdef- und .xml-Dateien öffnen. Visual Studio-Designs (.vstheme-Dateien) können mit dem Visual Studio-Erweiterungsfarb-Editor verwendet werden, indem Sie die Dateierweiterung in .xml ändern. Darüber hinaus können .vstheme-Dateien in eine aktuelle XML-Datei importiert werden.

 ![VSIX-Farb-Editor-Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX-Farb-Editor-Hero")

 **Paketdefinitionsdateien**

 Paketdefinitionsdateien (.pkgdef) sind die Dateien, die Designs definieren. Die Farben selbst werden in Theme Color .xml Dateien gespeichert, die in eine .pkgdef Datei kompiliert werden. Die .pkgdef-Dateien werden an durchsuchbaren Visual Studio-Speicherorten bereitgestellt, zur Laufzeit verarbeitet und zusammengeführt, um Designs zu definieren.

 **Farbtoken**

 Ein Farbtoken besteht aus vier Elementen:

- **Kategoriename:** Eine logische Gruppierung für einen Satz von Farben. Verwenden Sie einen vorhandenen Kategorienamen, wenn bereits Farben vorhanden sind, die für das gewünschte UI-Element oder eine Gruppe von UI-Elementen spezifisch sind.

- **Tokenname:** Ein beschreibender Name für die Farbtoken- und Tokensätze. Sets enthalten Hintergrund- und Vordergrundtokennamen (Text) sowie alle ihre Zustände, und diese sollten benannt werden, damit die Paare und die Zustände, auf die sie angewendet werden, leicht identifiziert werden können.

- **Farbwerte (oder Farbtöne):** Benötigt für jedes farbige Thema. Erstellen Sie immer Hintergrund- und Textfarbwerte in Paaren. Farben werden für Hintergrund/Vordergrund gepaart, sodass die Textfarbe (Vordergrundfarbe) immer vor der Hintergrundfarbe lesbar ist, auf der sie gezeichnet wird. Diese Farben sind verknüpft und werden zusammen in der Benutzeroberfläche verwendet. Wenn der Hintergrund nicht für die Verwendung mit Text vorgesehen ist, definieren Sie keine Vordergrundfarbe.

- **Systemfarbname:** Für den Einsatz in kontrastreichen Displays.

## <a name="how-to-use-the-tool"></a>Verwendung des Tools
 So viel wie möglich und gegebenenfalls vorhandene Visual Studio-Farben sollten wiederverwendet werden, anstatt neue zu erstellen. Für Fälle, in denen keine geeigneten Farben definiert sind, sollten jedoch benutzerdefinierte Farben erstellt werden, um eine Erweiterungs-Theming kompatibel zu halten.

 **Erstellen neuer Farbtoken**

 Gehen Sie folgendzulande vor, um benutzerdefinierte Farben mit dem Visual Studio-Erweiterungsfarb-Editor zu erstellen:

1. Bestimmen Sie die Kategorie- und Tokennamen für die neuen Farbtoken.

2. Wählen Sie die Farbtöne aus, die das UI-Element für jedes Design verwendet, und die Systemfarbe für hohen Kontrast.

3. Verwenden Sie den Farbeditor, um neue Farbtoken zu erstellen.

4. Verwenden Sie die Farben in einer Visual Studio-Erweiterung.

5. Testen Sie die Änderungen in Visual Studio.

   **Schritt 1: Bestimmen Sie die Kategorie- und Tokennamen für die neuen Farbtoken.**

   Das bevorzugte Benennungsschema für eine VSColor ist **[Kategorie] [UI-Typ] [Status]**. Verwenden Sie das Wort "farbe" nicht in VSColor-Namen, da es redundant ist.

   Kategorienamen stellen logische Gruppierungen bereit und sollten so eng wie möglich definiert werden. Der Name eines einzelnen Werkzeugfensters kann z. B. ein Kategoriename sein, der Name einer gesamten Unternehmenseinheit oder eines Projektteams jedoch nicht. Das Gruppieren von Einträgen in Kategorien hilft, Verwechslungen zwischen Farben mit demselben Namen zu vermeiden.

   Ein Tokenname muss eindeutig den Elementtyp und die Situationen oder den "Status" angeben, auf die die Farbe angewendet wird. Beispielsweise könnte der **[UI-Typ]** eines aktiven Datentipps den Namen **"DataTip**" und der **[Status]** **"Aktiv"** heißen, was zu einem Farbnamen von "**DataTipActive"** führt. Da Datentipps Text enthalten, müssen sowohl eine Vordergrund- als auch eine Hintergrundfarbe definiert werden. Durch die Verwendung einer Hintergrund-/Vordergrundpaarung erstellt der Farbeditor automatisch die Farben "**DataTipActive**" für den Hintergrund und "**DataTipActiveText**" für den Vordergrund.

   Wenn das Element der Benutzeroberfläche nur einen Zustand hat, kann der **[Status]-Teil** des Namens weggelassen werden. Wenn z. B. ein Suchfeld einen Rahmen hat und keine Zustandsänderung vorliegt, die sich auf die Farbe des Rahmens auswirken würde, kann der Name für das Farbtoken des Rahmens einfach als **"SearchBoxBorder"** bezeichnet werden.

   Einige gängige Statusnamen sind:

- Aktiv

- Inaktiv

- MouseOver

- Mousedown

- Aktiviert

- Mit Fokus

  Beispiele für einige Tokennamen für Teile eines Listenelementsteuerelements:

- ListItem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **Schritt 2: Wählen Sie die Farbtöne aus, die das UI-Element für jedes Design verwendet, und die Systemfarbe für hohen Kontrast.**

  Wenn Sie benutzerdefinierte Farben für die Benutzeroberfläche auswählen, wählen Sie ein ähnliches vorhandenes UI-Element aus, und verwenden Sie dessen Farben als Basis. Die Farben für in-the-box UI-Elemente wurden überprüft und getestet, so dass sie angemessen aussehen und sich in allen Designs korrekt verhalten.

  **Schritt 3: Verwenden Sie den Farbeditor, um neue Farbtoken zu erstellen.**

  Starten Sie den Farbeditor und öffnen oder erstellen Sie eine neue benutzerdefinierte Designfarben .xml-Datei. Wählen Sie **> Neue Farbe** bearbeiten aus dem Menü aus. Dadurch wird ein Dialogfeld zum Angeben der Kategorie und eines oder mehrere Namen für Farbeinträge innerhalb dieser Kategorie geöffnet:

  ![VSIX-Farb-Editor – Neue Farbe](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX-Farb-Editor – Neue Farbe")

  Wählen Sie eine vorhandene Kategorie aus, oder wählen Sie **Neue Kategorie** aus, um eine neue Kategorie zu erstellen. Ein weiteres Dialogfeld wird geöffnet, in dem ein neuer Kategoriename erstellt wird:

  ![VSIX-Farb-Editor – Neue Kategorie](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX-Farb-Editor – Neue Kategorie")

  Die neue Kategorie wird dann im Dropdown-Menü **"Neue Farbe"** verfügbar. Nachdem Sie eine Kategorie ausgewählt haben, geben Sie für jedes neue Farbtoken einen Namen pro Zeile ein, und wählen Sie "Erstellen", wenn Sie fertig sind:

  ![VSIX-Farb-Editor – Neue Farbe gefüllt](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX-Farb-Editor – Neue Farbe gefüllt")

  Die Farbwerte werden in Hintergrund-/Vordergrundpaaren angezeigt, wobei "Keine" angibt, dass die Farbe nicht definiert wurde. Hinweis: Wenn eine Farbe kein Textfarb-/Hintergrundfarbpaar hat, muss nur der Hintergrund definiert werden.

  ![VSIX-Farb-Editor-Farbwerte](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX-Farb-Editor-Farbwerte")

  Um ein Farbtoken zu bearbeiten, wählen Sie einen Farbeintrag für das Design (Spalte) dieses Tokens aus. Fügen Sie den Farbwert hinzu, indem Sie entweder einen Hex-Farbwert im 8-stelligen ARGB-Format eingeben, einen Systemfarbnamen in die Zelle eingeben oder das Dropdown-Menü verwenden, um die gewünschte Farbe über eine Reihe von Farbschiebereglern oder eine Liste von Systemfarben auszuwählen.

  ![VSIX-Farb-Editor Farbe bearbeiten](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX-Farb-Editor Farbe bearbeiten")

  ![VSIX-Farb-Editor – Hintergrund](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX-Farb-Editor – Hintergrund")

  Geben Sie für Komponenten, die keinen Text anzeigen müssen, nur einen Farbwert ein: die Hintergrundfarbe. Geben Sie andernfalls Werte für Hintergrund- und Textfarbe ein, die durch einen Schrägstrich getrennt sind.

  Geben Sie bei der Eingabe von Werten für hohen Kontrast gültige Windows-Systemfarbnamen ein. Geben Sie keine hartcodierten ARGB-Werte ein. Sie können eine Liste gültiger Systemfarbnamen anzeigen, indem Sie in den Dropdown-Menüs "Hintergrund: System" oder "Vordergrund: System" auswählen. Verwenden Sie beim Erstellen von Elementen mit Textkomponenten das richtige Hintergrund-/Textsystemfarbpaar, oder der Text ist möglicherweise nicht lesbar.

  Wenn Sie die Erstellung, Einstellung und Bearbeitung der Farbtoken abgeschlossen haben, speichern Sie sie im gewünschten .xml- oder .pkgdef-Format. Farbtoken mit weder Hintergrund noch Vordergrundsatz werden als leere Farben im XML-Format gespeichert, aber im .pkgdef-Format verworfen. Ein Dialogfeld warnt Sie vor einem möglichen Farbverlust, wenn Sie versuchen, leere Farben in einer Pkgdef-Datei zu speichern.

  **Schritt 4: Verwenden Sie die Farben in einer Visual Studio-Erweiterung.**

  Nachdem Sie die neuen Farbtoken definiert haben, fügen Sie die .pkgdef in die Projektdatei ein, wobei "Build Action" auf "Inhalt" und "In VSIX einschließen" auf "True" gesetzt ist.

  ![VSIX-Farb-Editor pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX-Farb-Editor pkgdef")

  Wählen Sie im Visual Studio-Erweiterungsfarb-Editor Datei > Ansichtsressourcencode aus, um Code anzuzeigen, der für den Zugriff auf die benutzerdefinierten Farben in der WPF-basierten Benutzeroberfläche verwendet wird.

  ![VSIX-Farb-Editor-Ressourcencode-Viewer](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX-Farb-Editor-Ressourcencode-Viewer")

  Fügen Sie diesen Code in eine statische Klasse in das Projekt ein. Ein Verweis auf **Microsoft.VisualStudio.Shell.\< VSVersion>.0.dll** muss dem Projekt hinzugefügt werden, um den **Typ ThemeResourceKey** zu verwenden.

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 Dies ermöglicht den Zugriff auf die Farben im XAML-Code und ermöglicht es der Benutzeroberfläche, auf Designänderungen zu reagieren.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **Schritt 5: Testen Sie die Änderungen in Visual Studio.**

 Der Farbeditor kann vorübergehend Farbtoken auf die ausgeführten Instanzen von Visual Studio anwenden, um Live-Änderungen an Farben anzuzeigen, ohne das Erweiterungspaket neu zu erstellen. Klicken Sie dazu auf die Schaltfläche "Anwenden dieses Themas auf das Ausführen von Visual Studio-Fenstern" in der Kopfzeile jeder Designspalte. Dieses temporäre Design wird verschwinden, wenn der VSIX-Farbeditor geschlossen wird.

 ![VSIX-Farb-Editor – Übernehmen](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX-Farb-Editor – Übernehmen")

 Um die Änderungen dauerhaft zu machen, erstellen Sie die Visual Studio-Erweiterung neu und stellen Sie sie erneut bereit, nachdem Sie die neuen Farben zur .pkgdef-Datei hinzugefügt und den Code geschrieben haben, der diese Farben verwendet. Durch das Erneute Erstellen der Visual Studio-Erweiterung werden die Registrierungswerte für die neuen Farben mit den übrigen Designs zusammengeführt. Starten Sie dann Visual Studio neu, zeigen Sie die Benutzeroberfläche an, und stellen Sie sicher, dass die neuen Farben wie erwartet angezeigt werden.

## <a name="notes"></a>Notizen
 Dieses Tool dient zum Erstellen benutzerdefinierter Farben für die bereits vorhandenen Visual Studio-Designs oder zum Bearbeiten der Farben eines benutzerdefinierten Visual Studio-Designs. Um vollständige benutzerdefinierte Visual Studio-Designs zu erstellen, laden Sie die [Erweiterung Visual Studio Color Theme Editor](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) aus der Visual Studio Extensions Gallery herunter.

## <a name="sample-output"></a>Beispielausgabe
 **XML-Farbausgabe**

 Die vom Tool generierte .xml-Datei ist wie folgt:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **PKGDEF Farbausgabe**

 Die vom Tool generierte .pkgdef-Datei ist wie folgt:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **Wrapper für Ressourcenschlüssel von Cé**

 Die vom Werkzeug generierten Farbressourcenschlüssel ähneln wie folgt:

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **WPF-Ressourcenwörterbuch-Wrapper**

 Die vom Tool generierten Color **ResourceDictionary-Schlüssel** ähneln wie folgt:

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```
