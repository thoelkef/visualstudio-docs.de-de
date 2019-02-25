---
title: Erstellen ein Randsteuerelement der Ansicht, Befehlen und -Einstellungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd5bfc24fcf1cd8a465bafe1e5bcf6c4df61308c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722290"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Exemplarische Vorgehensweise: Erstellen Sie eine Ansicht Zusatzelement, Befehle und Einstellungen)
Sie können die Visual Studio-Text, Code-Editor mit Befehlen und Anzeigen von Effekten erweitern. Diesem Artikel erfahren Sie, wie zum Einstieg in eine Funktion für beliebte Erweiterung Spaltenführungslinien können. Spaltenführungslinien werden visuell hell Zeilen, die auf den Text-Editor-Ansicht helfen Ihnen beim Verwalten von Code, um bestimmte Spaltenbreite gezeichnet. Insbesondere kann formatierten Code für Beispiele wichtig sein, Sie enthalten, die in Dokumenten, Blogbeiträgen oder Fehlerberichte, werden sollen.

In dieser exemplarischen Vorgehensweise Sie:
- Erstellen Sie ein VSIX-Projekt
- Fügen Sie ein Zusatzelement der Editor-Ansicht
- Hinzufügen von Unterstützung für das Speichern und Abrufen von Einstellungen (Ort von Zeichnen-Befehl Spaltenführungslinien und ihre Farbe)
- Hinzufügen von Befehlen (Spaltenführungslinien hinzufügen/entfernen, ändern Sie ihre Farbe)
- Platzieren Sie die Befehle auf dem Menü "Bearbeiten" und Text-Dokument-Kontextmenüs
- Hinzufügen von Unterstützung für die Befehle in der Visual Studio-Befehlsfenster aufrufen

  Sie können versuchen, eine Version von der Funktion "Spalte Guides" mit diesem Visual Studio Gallery[Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).

  **HINWEIS**: In dieser exemplarischen Vorgehensweise fügen Sie eine große Menge an Code, in einigen Dateien, die von Visual Studio-Extension-Vorlagen generiert. Aber in Kürze in dieser exemplarischen Vorgehensweise wird finden Sie eine vollständige Lösung auf GitHub mit anderen Beispielen für die Erweiterung. Der fertige Code unterscheidet sich geringfügig, dass es sich um echte Befehlssymbole anstelle von Generictemplate Symbole hat.

## <a name="get-started"></a>Erste Schritte
Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Einrichten der Lösung
Zunächst erstellen Sie ein VSIX-Projekt, ein Zusatzelement der Editor-Ansicht hinzufügen und fügen Sie dann einen Befehl (bei dem eine VSPackage, um den Befehl Besitzer hinzugefügt). Die grundlegende Architektur lautet wie folgt aus:
- Sie haben einen Text-Ansicht-erstellen-Listener, der erstellt eine `ColumnGuideAdornment` Objekt pro Ansicht. Dieses Objekt überwacht Ereignisse im Zusammenhang mit der Ansicht ändern, oder die Einstellungen ändern, aktualisieren oder das Neuzeichnen-Spalte führt nach Bedarf.
- Es gibt eine `GuidesSettingsManager` , verarbeitet werden, lesen und Schreiben von aus dem Speicher der Visual Studio-Einstellungen. Der Settings Manager verfügt auch über die Vorgänge zum Aktualisieren der Einstellungen, die der Benutzerbefehle unterstützen (Spalte hinzufügen, entfernen Sie die Spalte, ändern Sie die Farbe).
- Es ist ein VSIP-Paket, das ist erforderlich, wenn Sie Benutzerbefehle haben, aber es ist nur für den Standardcode, der die Befehle Implementierungsobjekt initialisiert.
- Gibt es eine `ColumnGuideCommands` -Objekt, das der Benutzer führt Befehle und verknüpft die Befehlshandler für die deklarierten Befehle in der *VSCT* Datei.

  **VSIX**. Verwendung **Datei &#124; neu...**  Befehl aus, um ein Projekt zu erstellen. Wählen Sie die **Erweiterbarkeit** Knoten unter **c#** im linken Navigationsbereich, und wählen Sie **VSIX-Projekt** im rechten Bereich. Geben Sie den Namen **ColumnGuides** , und wählen Sie **OK** zum Erstellen des Projekts.

  **Anzeigen des Zusatzelements**. Drücken Sie die Zeiger nach rechts auf den Projektknoten im Projektmappen-Explorer. Wählen Sie die **hinzufügen &#124; neues Element...**  Befehl aus, um ein neues Ansicht Zusatzelement Element hinzuzufügen. Wählen Sie **Erweiterbarkeit &#124; Editor** im linken Navigationsbereich, und wählen Sie **Editor Viewport Zusatzelement** im rechten Bereich. Geben Sie den Namen **ColumnGuideAdornment** als Element benennen, und wählen **hinzufügen** hinzugefügt.

  Sie können sehen, dass diese Elementvorlage zwei Dateien dem Projekt (sowie Verweise usw.) hinzugefügt: **ColumnGuideAdornment.cs** und **ColumnGuideAdornmentTextViewCreationListener.cs**. Die Vorlagen zeichnen eine violette Rechteck für die Sicht. Im folgenden Abschnitt, ändern Sie ein paar Codezeilen in der Ansicht erstellen Listener, und ersetzen den Inhalt der **ColumnGuideAdornment.cs**.

  **Befehle**. In **Projektmappen-Explorer**, drücken Sie die Zeiger nach rechts-Taste auf den Projektknoten. Wählen Sie die **hinzufügen &#124; neues Element...**  Befehl aus, um ein neues Ansicht Zusatzelement Element hinzuzufügen. Wählen Sie **Erweiterbarkeit &#124; VSPackage** im linken Navigationsbereich, und wählen Sie **benutzerdefinierten Befehls** im rechten Bereich. Geben Sie den Namen **ColumnGuideCommands** als Element benennen, und wählen **hinzufügen**. Zusätzlich zur mehrere Verweise, hinzufügen, die Befehle und das Paket auch hinzugefügt **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**, und **ColumnGuideCommandsPackage.vsct** . Im folgenden Abschnitt ersetzen Sie den Inhalt der ersten und letzten Dateien zu definieren und implementieren Sie die Befehle aus.

## <a name="set-up-the-text-view-creation-listener"></a>Einrichten des textlisteners der Ansicht erstellen
Open *ColumnGuideAdornmentTextViewCreationListener.cs* im Editor. Dieser Code wird ein Handler implementiert, für jedes Mal, wenn Visual Studio Textansichten erstellt. Es gibt Attribute an, mit denen gesteuert wird, wenn der Handler aufgerufen wird, abhängig von den Eigenschaften der Ansicht.

Der Code muss auch eine Zusatzelementebene deklarieren. Wenn der Editor Sichten aktualisiert, ruft der Zusatzelementebenen, die für die Ansicht und ruft aus, die die Elemente des Zusatzelements ab. Sie können deklarieren, die Reihenfolge der der Ebene relativ zu anderen Attribute. Ersetzen Sie die folgende Zeile:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

mit diesen zwei Zeilen:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Die Zeile der nun ersetzte ist in einer Gruppe von Attributen, die eine Zusatzelementebene deklarieren. Die erste Zeile ändern Sie nur die Änderungen, die Führungslinien Spalte angezeigt werden. Zeichnen von Linien "vor" der Text in der Ansicht bedeutet, dass sie hinter oder unterhalb des Texts angezeigt werden. Die zweite Zeile deklariert, dass die Spalte Handbuch Zusatzelemente gelten für Text-Entitäten, die Ihr Konzept eines Dokuments anpassen, aber Sie können dem Zusatzelement befindet, z. B. um funktioniert nur für die bearbeitbaren Text deklarieren. Es gibt weitere Informationen im [Language Service und -Editor-Erweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Implementieren der Settings manager
Ersetzen Sie den Inhalt von der *GuidesSettingsManager.cs* durch den folgenden Code (siehe nachfolgende Erläuterung):

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

Die meisten dieser Code erstellt und analysiert das Format der Konfigurationseinstellungen: "RGB (\<Int >,\<Int >,\<Int >) \<Int >, \<Int >,...".  Die ganzen Zahlen am Ende handelt es sich um die Spalten eins Spaltenführungslinien sollen. Die Spalte-Anleitungen-Erweiterung erfasst alle Einstellungen für die in eine einzelne Einstellung-Wert-Zeichenfolge.

Es gibt einige Teile des Codes zu markieren. Die folgende Codezeile ruft der verwaltete Wrapper für Visual Studio für die Speicherung der Einstellungen ab. Zum größten Teil, wird dies über die Windows-Registrierung abstrahiert, aber diese API ist unabhängig von den Speichermechanismus.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Der Speicher der Visual Studio-Einstellungen verwendet ein Kategorie-ID und einer Einstellung-ID zur eindeutigen Identifizierung der alle Einstellungen:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Sie müssen keine verwenden `"Text Editor"` als Namen der Kategorie. Sie können Alles auswählen, die Ihnen gefällt.

Die ersten Paar Funktionen sind die Einstiegspunkte, um Einstellungen zu ändern. Sie überprüfen die allgemeine Einschränkungen wie die maximale Anzahl von Anleitungen, die zulässig.  Sie rufen Sie dann `WriteSettings`, die eine einstellungszeichenfolge verfasst und legt die Eigenschaft `GuideLinesConfiguration`. Durch Festlegen dieser Eigenschaft speichert den Einstellungswert der Visual Studio-einstellungsspeicher und löst die `SettingsChanged` Ereignis, um alle aktualisieren die `ColumnGuideAdornment` Objekten, die jeweils eine Textansicht zugeordnet.

Es gibt eine Reihe von Funktionen für Posten, z.B. `CanAddGuideline`, die werden verwendet, um Befehle zu implementieren, die Einstellungen zu ändern. Wenn Menüs in Visual Studio angezeigt wird, fragt es befehlsimplementierung, um festzustellen, ob der Befehl derzeit aktiviert ist, was ist der Name und So weiter.  Im folgenden sehen Sie, wie diese Einstiegspunkte für die befehlsimplementierung verknüpft. Weitere Informationen zu Befehlen finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementieren Sie die ColumnGuideAdornment-Klasse
Die `ColumnGuideAdornment` für jede Textansicht Zusatzelemente, die denen Klasse instanziiert wird. Diese Klasse überwacht Ereignisse, die über die Ansicht ändern oder Ändern von Einstellungen sowie das Aktualisieren oder das Neuzeichnen Spaltenführungslinien nach Bedarf.

Ersetzen Sie den Inhalt von der *ColumnGuideAdornment.cs* durch den folgenden Code (siehe nachfolgende Erläuterung):

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

Instanzen dieser Klasse enthalten, auf die zugeordnete <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> und eine Liste der `Line` Objekte, die für die Sicht gezeichnet.

Der Konstruktor (von aufgerufen `ColumnGuideAdornmentTextViewCreationListener` bei Visual Studio erstellt neue Ansichten) im Handbuch für die Spalte erstellt `Line` Objekte.  Der Konstruktor fügt auch Handler für die `SettingsChanged` Ereignis (definiert `GuidesSettingsManager`) und die sichtereignisse `LayoutChanged` und `Closed`.

Die `LayoutChanged` -Ereignis ausgelöst wird, aufgrund von verschiedenen Arten von Änderungen in der Ansicht, die auch bei der Visual Studio die Ansicht erstellt. Die `OnViewLayoutChanged` handleraufrufen `AddGuidelinesToAdornmentLayer` ausgeführt. Der Code in `OnViewLayoutChanged` bestimmt, ob die Zeile positioniert, die basierend auf Änderungen wie Änderungen, Ansicht Bundstege, horizontales scrollen und So weiter aktualisiert werden muss. Der Code in `UpdatePositions` bewirkt, dass Führungslinien, um zwischen Zeichen oder unmittelbar nach der Spalte der Text, der in der angegebenen Zeichenoffset in der Zeile des Texts zu zeichnen.

Bei jedem Ändern der Einstellungen der `SettingsChanged` Funktion wird nur erstellt, alle der `Line` Objekte mit die für die neuen Einstellungen werden. Nach dem Festlegen der Zeile positioniert, der Code entfernt alle vorherigen `Line` Objekte aus der `ColumnGuideAdornment` Zusatzelementebene und die neuen Dateien hinzugefügt.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definieren Sie die Befehle, Menüs und Menü Platzierungen
Es kann sein viel, deklarieren, Befehle und Menüs, platzieren Gruppen von Befehlen oder Menüs auf verschiedenen anderen Menüs und befehlshandlern einbinden. In dieser exemplarischen Vorgehensweise werden hervorgehoben, wie Befehle in dieser Erweiterung, aber für umfangreichere Informationen funktionieren, finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Einführung in den code
Die Erweiterung Spaltenführungslinien zeigt deklarieren eine Gruppe von Befehlen, die zusammengehören (Spalte hinzufügen, entfernen Sie die Spalte, ändern Sie die Linienfarbe), und klicken Sie dann dieser Gruppe auf einem Untermenü des Kontextmenüs des Editors zu platzieren.  Die Spaltenführungslinien Erweiterung fügt auch die Befehle an den Hauptserver **bearbeiten** Menü jedoch hält sie nicht sichtbar ist, als ein allgemeines Muster, die weiter unten erläutert.

Es gibt drei Teile der Implementierung der Befehle aus: ColumnGuideCommandsPackage.cs ColumnGuideCommandsPackage.vsct und ColumnGuideCommands.cs. Der Code generiert, die von den Vorlagen stellt einen Befehl in der **Tools** Menü, das ein als Implementierung Dialogfeld. Sehen Sie sich, die Implementierung von in die *VSCT* und *ColumnGuideCommands.cs* Dateien, da es einfach ist. Sie ersetzen den Code in diesen Dateien, die weiter unten.

Der Paketcode enthält Codebausteine Deklarationen für Visual Studio erforderlich sind, um zu ermitteln, dass die Erweiterung, Befehle bietet und platzieren Sie die Befehle finden. Wenn das Paket initialisiert wird, instanziiert er die Implementierungsklasse Befehle. Weitere Informationen zu Paketen, die im Zusammenhang mit Befehlen, finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Ein häufiges Muster für die Befehle
Die Befehle in der Erweiterung Spaltenführungslinien sind ein Beispiel für ein weit verbreitetes Muster in Visual Studio. Sie verwandte Befehle in einer Gruppe platzieren, und stellen diese Gruppe auf ein Hauptmenü, häufig mit "`<CommandFlag>CommandWellOnly</CommandFlag>`" festgelegt werden, um den Befehl unsichtbar zu machen.  Platzieren Befehle auf den Hauptmenüs (z. B. **bearbeiten**) erhalten sie eine gute Namen (z. B. **Edit.AddColumnGuide**), eignen sich für die Suche nach Befehlen, wenn tastenzuordnungen in neu zuweisen **Tools Optionen**. Es ist auch hilfreich zum Abrufen der Vervollständigung beim Aufruf von Befehlen aus der **Befehlsfenster**.

Klicken Sie anschließend die Gruppe von Befehlen zu Kontextmenüs hinzufügen oder sub-Menüs, in denen erwartungsgemäß Benutzer, die Befehle zu verwenden. Visual Studio behandelt `CommandWellOnly` als ein unsichtbarkeits-Flag für nur den Hauptmenüs. Wenn Sie die gleiche Gruppe von Befehlen auf einem Kontextmenü oder Untermenü platzieren, sind die Befehle angezeigt.

Als Teil eines allgemeinen Musters erstellt die Spaltenführungslinien-Erweiterung eine zweite Gruppe, die einen einzelnen Untermenü enthält. Das Untermenü enthält wiederum die erste Gruppe mit den Befehlen vierspaltige-Handbuch. Die zweite Gruppe, die das Untermenü enthält, ist die wiederverwendbare Asset, die Sie für verschiedene Kontextmenüs, an die setzt ein Sub-Menü auf die Kontextmenüs.

### <a name="the-vsct-file"></a>Der VSCT-Datei
Die *VSCT* Datei deklariert die Befehle und, zusammen mit Symbolen und wo sie. Ersetzen Sie den Inhalt von der *VSCT* -Datei mit den folgenden Code (siehe nachfolgende Erläuterung):

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**GUIDS**. Für Visual Studio zum Suchen der Befehlshandler und rufen diese, müssen Sie die Paket-GUID, die im deklarierten Sicherstellen der *ColumnGuideCommandsPackage.cs* Datei (aus der Projektelementvorlage generiert) entspricht, das Paket mit dem GUID in deklariert die *VSCT* (von oben kopierte) Datei. Wenn Sie diesen Beispielcode erneut verwenden, sollten Sie sicherstellen, dass Sie eine andere GUID haben, sodass Sie nicht mit anderen Person in Konflikt stehen, die diesen Code kopiert haben, können.

Suchen Sie nach dieser Zeile im *ColumnGuideCommandsPackage.cs* und kopieren Sie die GUID von einschließlich der Anführungszeichen:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Fügen Sie dann auf die GUID in der *VSCT* Datei, sodass Sie die folgende Zeile Ihrer `Symbols` Deklarationen:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Legen Sie die GUIDs für den Befehl aus, und die Bitmap-Bilddatei muss zu den Erweiterungen, eindeutig sein:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Aber Sie müssen nicht den Befehlssatz zu ändern und die bitmap-Bild-GUIDs in dieser exemplarischen Vorgehensweise zum Abrufen des Codes funktioniert. Den Befehlssatz, der GUID entsprechend die Deklaration in muss der *ColumnGuideCommands.cs* ersetzen Sie den Inhalt der Datei, Sie aber zu; aus diesem Grund sind die GUIDs entspricht.

Andere GUIDs in der *VSCT* Datei zu bereits vorhandenen Menüs, der die Spalte-Guide-Befehle hinzugefügt werden, identifizieren, sodass sie nie ändern.

**Datei Abschnitte**. Die *VSCT* ist drei äußeren Abschnitte unterteilt: Befehle, Platzierungen und Symbole. Im Abschnitt Befehle definiert, Befehlsgruppen, Menüs, Schaltflächen oder Menüelemente und Bitmaps für Symbole. Abschnitt Platzierungen deklariert, wo der Gruppen auf Menüs oder zusätzliche Platzierungen auf bereits vorhandenen Menüs. Der Abschnitt "Symbols" deklariert den Bezeichner, die an anderer Stelle verwendet werden, der *VSCT* -Datei, die macht der *VSCT* Code besser lesbar als GUIDs und hexadezimale Ziffern überall.

**Befehle im Abschnitt, Gruppen oder Definitionen**. Im Abschnitt Befehle definiert zunächst Befehlsgruppen. Gruppen von Befehlen handelt es sich um Menübefehle in Menüs mit geringfügigen grauen Linien, die die Gruppen zu trennen. Eine Gruppe kann eine gesamte Untermenü, wie im folgenden Beispiel, Felder aus, und die grauen Trennen von Zeilen in diesem Fall nicht angezeigt. Die *VSCT* Dateien deklariert zwei Gruppen, die `GuidesMenuItemsGroup` , übergeordnet ist die `IDM_VS_MENU_EDIT` (Hauptfenster **bearbeiten** im Menü) und die `GuidesContextMenuGroup` , übergeordnet ist die `IDM_VS_CTXT_CODEWIN` (der Code Anmerkung der Redaktion Kontextmenü).

Die zweite Gruppendeklaration hat einen `0x0600` Priorität:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Die Idee ist die-Spalte einzufügenden Untermenü am Ende führt der ein Kontextmenü zu dem Sie die Sub-Menü-Gruppe hinzufügen. Aber, dass Sie nicht annehmen, Sie am besten kennen und erzwingen das Untermenü immer das letzte ist mit einer Priorität von `0xFFFF`. Experimentieren mit der Anzahl, um anzuzeigen, in dem das Sub-Menü auf die Kontextmenüs liegt, wo Sie es platzieren, müssen. In diesem Fall `0x0600` ist hoch genug ist, als Sie sehen, lässt jedoch auch Raum für jemand anderen entwerfen Sie ihre Erweiterung, die nicht niedriger als die Spalte Guides-Erweiterung, ggf. die am Ende des Menüs ausgedrückt.

**Befehle Abschnitt menüdefinition**. Als Nächstes im Abschnitt-Befehl definiert das Sub-Menü `GuidesSubMenu`, übergeordnetes Element, um die `GuidesContextMenuGroup`. Die `GuidesContextMenuGroup` ist die Gruppe, die Sie, die relevanten Kontextmenüs hinzufügen. Klicken Sie im Abschnitt Platzierungen platziert der Code die Gruppe mit den vier Spalten-Guide-Befehlen in diesem Sub-Menü.

**Befehle im Abschnitt, Schaltflächen Definitionen**. Im Abschnitt Befehle definiert klicken Sie dann die Menüelemente oder Schaltflächen, die die vier Spalten Guides-Befehle sind. `CommandWellOnly`, weiter oben erläuterten, bedeutet, dass die Befehle sind nicht sichtbar, wenn es auf einem Hauptmenü stammt platziert. Zwei der dem Menüelement, das Deklarationen Schaltfläche (Handbuch hinzufügen und entfernen Sie die Anleitung) auch eine `AllowParams` Flag:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Dieses Flag ermöglicht es, zusammen mit Hauptmenü Platzierungen, den Befehl aus, um Argumente zu erhalten, wenn Visual Studio der Befehlshandler ruft.  Wenn der Benutzer den Befehl aus dem Befehlsfenster ausgeführt wird, wird das Argument an den Befehlshandler in dieser Argumente übergeben.

**Befehl Abschnitten, Bitmaps Definitionen**. Abschließend deklariert die Befehle im Abschnitt auf, die Bitmaps oder Symbole, die für die Befehle verwendet. Dieser Abschnitt ist eine einfache Deklaration, die die Projektressource identifiziert, und listet 1 basierenden Indizes verwendeten Symbole. Der Abschnitt "Symbols" von der *VSCT* Datei deklariert die Werte als Indizes verwendeten Bezeichner. In dieser exemplarischen Vorgehensweise verwendet den bitmapstrip zur Verfügung gestellt, mit den benutzerdefinierten Befehl Elementvorlage zum Projekt hinzugefügt.

**Platzierungen Abschnitt**. Nach den Befehlen bildet den Platzierungen-Abschnitt. Der erste Parameter ist, in dem der Code fügt hinzu, dass die erste Gruppe, die hier erläutert, die im Handbuch für die vier Spalten enthält Befehle aus, um das Untermenü angezeigt werden, in dem die Befehle aus:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Alle der anderen Standorte hinzufügen, die `GuidesContextMenuGroup` (enthält die `GuidesSubMenu`) auf andere Editor-Kontextmenüs. Wenn der Code deklariert die `GuidesContextMenuGroup`, es wurde der Code-Editor-Kontextmenü übergeordnet. Deshalb eine Platzierung für die Code-Editor-Kontextmenü nicht angezeigt.

**Symbole im Abschnitt**. Wie bereits erwähnt, deklariert den Abschnitt "Symbols" Bezeichner, die an anderer Stelle verwendet werden, der *VSCT* -Datei, die macht der *VSCT* Code besser lesbar als GUIDs und hexadezimale Ziffern überall. Die wichtigen Punkte in diesem Abschnitt sind, dass die GUID des Pakets mit der Deklaration in der Paketklasse zustimmen muss. Und der Befehlssatz-GUID muss mit der Deklaration in der Klasse des Befehls Implementierung übereinstimmen.

## <a name="implement-the-commands"></a>Implementieren Sie die Befehle
Die *ColumnGuideCommands.cs* -Datei implementiert die Befehle und die Handler verknüpft. Wenn Visual Studio wird das Paket geladen und wird initialisiert, ruft das Paket im Gegenzug `Initialize` auf der Implementierungsklasse Befehle. Die Initialisierung der Befehle einfach instanziiert die Klasse, und der Konstruktor die Befehlshandler verknüpft.

Ersetzen Sie den Inhalt von der *ColumnGuideCommands.cs* -Datei mit den folgenden Code (siehe nachfolgende Erläuterung):

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**Korrektur von verweisen**. Sie können einen Verweis an diesem Punkt fehlt. Drücken Sie die Zeiger nach rechts auf den Knoten "Verweise" im Projektmappen-Explorer. Wählen Sie die **hinzufügen...**  Befehl. Die **Verweis hinzufügen** Dialog besitzt ein Suchfeld in der oberen rechten Ecke. Geben Sie "Editor" (ohne Anführungszeichen) ein. Wählen Sie die **Microsoft.VisualStudio.Editor** Element (Sie müssen aktivieren Sie das Kontrollkästchen auf der linken Seite des Elements nicht einfach auf das Element), und wählen Sie **OK** um den Verweis hinzuzufügen.

**Initialisierung**.  Wenn die Paketklasse initialisiert wird, ruft er `Initialize` auf der Implementierungsklasse Befehle. Die `ColumnGuideCommands` Initialisierung instanziiert die Klasse und die Instanz der Klasse und den Paketverweis in-Klasse, Elemente gespeichert.

Sehen wir uns eine der Befehl Handler Hook-USV vom Konstruktor Klasse:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Sie erstellen eine `OleMenuCommand`. Visual Studio verwendet das Microsoft Office-System-Befehl. Wichtige Argumente bei der Instanziierung einer `OleMenuCommand` ist die Funktion, die der Befehl implementiert (`AddColumnGuideExecuted`), die Funktion, die aufgerufen werden, wenn Visual Studio ein Menü mit dem Befehl zeigt (`AddColumnGuideBeforeQueryStatus`), und die Befehls-ID. Visual Studio Ruft die Abfragefunktion für den Status vor dem Anzeigen eines Befehls in einem Menü, damit der Befehl selbst nicht sichtbar oder für eine bestimmte Darstellung des Menüs abgeblendeter kann (z. B. deaktivieren **Kopie** , wenn keine Auswahl vorhanden ist), Ändern Sie das Symbol, oder sogar ändern Sie den Namen (z. B. vom hinzufügen, entfernen Sie ein), und so weiter. Die Befehls-ID muss einen Befehl, der ID in deklariert entsprechen den *VSCT* Datei. Fügen Sie die Zeichenfolgen für den Befehlssatz, und die Spaltenführungslinien hinzu Befehl muss die gleiche der *VSCT* Datei und die *ColumnGuideCommands.cs*.

Die folgende Zeile bietet Unterstützung für, wenn Benutzer den Befehl über das Fenster "Befehl" (siehe nachfolgende Erläuterung) aufrufen:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Abfragen des Status**. Die Status-Abfragefunktionen `AddColumnGuideBeforeQueryStatus` und `RemoveColumnGuideBeforeQueryStatus` überprüfen Sie einige Einstellungen (z. B. die maximale Anzahl von Führungslinien oder max-Spalte) oder wenn eine Spalte-Anleitung zum Entfernen vorhanden ist. Sie ermöglichen die Befehle aus, wenn die Bedingungen richtig sind.  Status der Abfragefunktionen müssen effizient, da sie jedes Mal, zeigt Visual Studio ein Menü, und für jeden Befehl führen Sie im Menü.

 **AddColumnGuideExecuted Funktion**. Der interessante Teil beim Hinzufügen der Leitfaden ist, den aktuellen Editor-Ansicht und der Einfügemarke Speicherort herauszufinden.  Diese Funktion zunächst ruft `GetApplicableColumn`, die überprüft, ob ein Benutzer bereitgestelltes Argument in den Befehlshandler Ereignisargumente vorliegt und wenn keiner vorhanden ist, die Funktion des Editors anzeigen überprüft:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` ist ein wenig abzurufenden genauer ein <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> Ansicht des Codes.  Wenn Sie über die Ablaufverfolgung `GetActiveTextView`, `GetActiveView`, und `GetTextViewFromVsTextView`, sehen Sie, wie das geht. Der folgende Code ist der relevante Code abstrahiert, beginnend mit der aktuellen Auswahl, die Auswahl des Frames abrufen und dann beim Abrufen des Frames DocView-als ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, abgerufen werden. dann eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> aus der IVsTextView Abrufen eines Hosts anzeigen und schließlich die "IWpfTextView":

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

Nachdem Sie eine "IWpfTextView" haben, erhalten Sie die Spalte auf dem sich die Einfügemarke befindet:

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

Mit der aktuellen Spalte, die der Benutzer geklickt hat, ruft hand der Code nur auf die einstellungs-Manager hinzufügen oder entfernen Sie die Spalte. Der Settings Manager löst das Ereignis zu der alle `ColumnGuideAdornment` Objekte zu lauschen. Wenn das Ereignis ausgelöst wird, aktualisieren Sie diese Objekte ihre Ansichten zugeordneten Text mit neue spalteneinstellungen Handbuch.

## <a name="invoke-command-from-the-command-window"></a>Befehl "im Befehlsfenster" aufrufen
Die Handbücher spaltenstichprobe kann Benutzer zwei Befehle aus dem Befehlsfenster als eine Form der Erweiterung aufzurufen. Bei Verwendung der **Ansicht &#124; Other Windows &#124; Befehlsfenster** Befehls sehen Sie das Befehlsfenster. Sie können das Befehlsfenster interagieren, durch Eingabe von "Bearbeiten", und mit Befehl Vervollständigung von Objektnamen, und das Argument 120 bereitstellt, haben Sie das folgende Ergebnis:

```csharp
> Edit.AddColumnGuide 120
>
```

Die Teile des Beispiels, die dieses Verhalten zu aktivieren, sind in der *VSCT* Datei Deklarationen, die `ColumnGuideCommands` Klassenkonstruktor, wenn diese Befehlshandler und die befehlsimplementierung für Handler, die die Ereignisargumente prüfen verknüpft.

Sie haben gesehen, "`<CommandFlag>CommandWellOnly</CommandFlag>`" in der *VSCT* sowie Platzierungen in Datei der **bearbeiten** Hauptmenü, obwohl die Befehle nicht angezeigt werden, in der **bearbeiten** Menü UI. Müssen sie auf der Hauptseite **bearbeiten** -Menü können sie Namen wie z. B. **Edit.AddColumnGuide**. Die Deklaration der Befehle-Gruppe, die die vier Befehle enthält die Gruppe auf platziert die **bearbeiten** Menü direkt:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Der Schaltflächen-Abschnitt später deklariert die Befehle `CommandWellOnly` unsichtbar im Hauptmenü behalten möchten und diese mit deklarierten `AllowParams`:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Sie haben gesehen, die den Befehlshandler Einbinden von Code in die `ColumnGuideCommands` Klassenkonstruktor bereitgestellt, eine Beschreibung des Parameters zulässig:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Sie haben gesehen, die `GetApplicableColumn` -Funktion überprüft `OleMenuCmdEventArgs` für einen Wert vor der Überprüfung der Editoransicht für eine aktuelle Spalte:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>Wiederholen Sie die Erweiterung
Sie können jetzt drücken **F5** Ihre Spaltenführungslinien-Erweiterung ausgeführt. Öffnen Sie eine Textdatei, und verwenden Sie im Editor-Kontextmenü, um Führungslinien hinzufügen, entfernen Sie sie und ihre Farbe zu ändern. Klicken Sie in den Text (nicht-Leerzeichen übergeben das Ende der Zeile) hinzufügen eine Spalte Handbuch oder im Editor wird in die letzte Spalte in der Zeile. Wenn Sie das Befehlsfenster, und die Befehle mit einem Argument aufrufen, können Sie eine beliebige Stelle Spaltenführungslinien hinzufügen.

Wenn Sie verwenden möchten, versuchen Sie es anderen befehlsplatzierungen, ändern Sie Namen, Symbole usw. zu ändern und Sie haben Probleme mit Visual Studio den neuesten Code in den Menüs angezeigt, können Sie die experimentelle Struktur zurücksetzen, in der Sie debuggen. Rufen Sie die **Windows-Startmenü** , und geben Sie "Zurücksetzen". Suchen Sie nach, und führen Sie den Befehl **Zurücksetzen der nächsten Visual Studio experimentelle Instanz**. Dieser Befehl bereinigt alle Komponenten der Erweiterung der experimentellen Registrierungsstruktur ab. Nicht bereinigen Sie die Einstellungen von Komponenten, daher Anleitungen, die Sie beim Herunterfahren von Visual Studio in der experimentellen Struktur haben sind weiterhin vorhanden, wenn Ihr Code den einstellungsspeicher beim nächsten Start liest.

## <a name="finished-code-project"></a>Fertig gestellten Code-Projekt
Es ist bald ein GitHub-Projekt von Visual Studio-Erweiterbarkeit-Beispielen, und das abgeschlossene Projekt benötigen, ist vorhanden. In diesem Artikel wird aktualisiert werden, um es zu zeigen, wenn dies der Fall ist. Das abgeschlossene Beispielprojekt möglicherweise andere Guids und erhalten einen Streifen unterschiedliche Bitmaps, Symbole Befehl.

Sie können versuchen, eine Version von der Funktion "Spalte Guides" mit diesem Visual Studio Gallery[Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).

## <a name="see-also"></a>Siehe auch
- [Im editor](../extensibility/inside-the-editor.md)
- [Erweitern Sie die Dienste, Editoren und Sprachen](../extensibility/extending-the-editor-and-language-services.md)
- [Language-Dienst und -Editor-Erweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)
- [Erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)
