---
title: Erstellen einer Ansichtsverzierung, Befehle und Einstellungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aab9e0ede95eebe6f8f54cc3f01e7e7d5f98d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697646"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Exemplarische Vorgehensweise: Erstellen einer Ansichtsverzierung, Befehle und Einstellungen (Spaltenführungslinien)
Sie können den Visual Studio-Text-/Code-Editor um Befehle und Ansichtseffekte erweitern. Dieser Artikel zeigt Ihnen, wie Sie mit einer beliebten Erweiterungsfunktion, Spaltenhandbüchern, beginnen. Spaltenhilfslinien sind visuell lichtende Linien, die in der Ansicht des Texteditors gezeichnet werden, um Ihnen zu helfen, Ihren Code für bestimmte Spaltenbreiten zu verwalten. Insbesondere kann formatierter Code für Beispiele wichtig sein, die Sie in Dokumente, Blogbeiträge oder Fehlerberichte aufnehmen.

In dieser exemplarischen Vorgehensweise führen Sie folgende Aktionen aus:
- Erstellen eines VSIX-Projekts
- Hinzufügen einer Editoransichtsverzierung
- Unterstützung zum Speichern und Abrufen von Einstellungen hinzufügen (wo Spaltenführungen und deren Farbe gezeichnet werden sollen)
- Befehle hinzufügen (Spaltenhilfslinien hinzufügen/entfernen, Farbe ändern)
- Platzieren der Befehle im Menü "Bearbeiten" und in den Kontextmenüs des Textdokuments
- Hinzufügen von Unterstützung für das Aufrufen der Befehle aus dem Visual Studio-Befehlsfenster

  Mit dieser Visual Studio[Gallery-Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)können Sie eine Version des Column Guides-Features ausprobieren.

  > [!NOTE]
  > In dieser exemplarischen Vorgehensweise fügen Sie eine große Menge an Code in einige Dateien ein, die von Visual Studio-Erweiterungsvorlagen generiert werden. Aber bald wird diese exemplarische Vorgehensweise auf eine abgeschlossene Lösung auf GitHub mit anderen Erweiterungsbeispielen verweisen. Der abgeschlossene Code unterscheidet sich geringfügig dadurch, dass er echte Befehlssymbole hat, anstatt generische Vorlagensymbole zu verwenden.

## <a name="get-started"></a>Erste Schritte
Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Einrichten der Lösung
Zuerst erstellen Sie ein VSIX-Projekt, fügen eine Editoransichtsverzierung hinzu und fügen dann einen Befehl hinzu (der ein VSPackage zum Besitz des Befehls hinzufügt). Die grundlegende Architektur ist wie folgt:
- Sie verfügen über einen Textansichtserstellungslistener, der ein `ColumnGuideAdornment` Objekt pro Ansicht erstellt. Dieses Objekt überwacht Ereignisse, bei der die Ansicht geändert oder Einstellungen bei Bedarf geändert, aktualisiert oder neu gezeichnet werden.
- Es gibt `GuidesSettingsManager` eine, die das Lesen und Schreiben aus dem Visual Studio-Einstellungen-Speicher behandelt. Der Einstellungs-Manager verfügt auch über Vorgänge zum Aktualisieren der Einstellungen, die die Benutzerbefehle unterstützen (Spalte hinzufügen, Spalte entfernen, Farbe ändern).
- Es gibt ein VSIP-Paket, das erforderlich ist, wenn Sie Benutzerbefehle haben, aber es ist nur Boilerplate-Code, der das Befehlsimplementierungsobjekt initialisiert.
- Es gibt `ColumnGuideCommands` ein Objekt, das die Benutzerbefehle ausführt und die Befehlshandler für Befehle einhängt, die in der *.vsct-Datei* deklariert sind.

  **VSIX**. Verwenden Sie den Befehl **File &#124; New ...** , um ein Projekt zu erstellen. Wählen Sie im linken Navigationsbereich den **Erweiterbarkeitsknoten** unter **"C"** aus, und wählen Sie Im rechten Bereich **VSIX-Projekt** aus. Geben Sie den Namen **ColumnGuides** ein, und wählen Sie **OK** aus, um das Projekt zu erstellen.

  **Ansicht Sadornment**. Drücken Sie die rechte Zeigertaste auf dem Projektknoten im Projektmappen-Explorer. Wählen Sie den Befehl **&#124; Neues Element hinzufügen ...** aus, um ein neues Ansichtsschmuckelement hinzuzufügen. Wählen Sie **Erweiterbarkeit &#124;-Editor** im linken Navigationsbereich und im rechten Bereich **Editor-Ansichtsfenster-Schmuck** aus. Geben Sie den Namen **ColumnGuideAdornment** als Elementnamen ein, und wählen Sie **Hinzufügen** aus, um ihn hinzuzufügen.

  Sie können sehen, dass diese Elementvorlage dem Projekt zwei Dateien hinzugefügt hat (sowie Verweise usw.): **ColumnGuideAdornment.cs** und **ColumnGuideAdornmentTextViewCreationListener.cs**. Die Vorlagen zeichnen ein violettes Rechteck in der Ansicht. Im folgenden Abschnitt ändern Sie einige Zeilen im Ansichtserstellungslistener und ersetzen den Inhalt **von ColumnGuideAdornment.cs**.

  **Befehle**. Drücken Sie im **Projektmappen-Explorer**die rechte Zeigertaste auf dem Projektknoten. Wählen Sie den Befehl **&#124; Neues Element hinzufügen ...** aus, um ein neues Ansichtsschmuckelement hinzuzufügen. Wählen Sie **Erweiterbarkeit &#124; VSPackage** im linken Navigationsbereich und im rechten Bereich **benutzerdefinierter Befehl** aus. Geben Sie den Namen **ColumnGuideCommands** als Elementnamen ein, und wählen Sie **Hinzufügen**aus. Zusätzlich zu mehreren Verweisen wurden die Befehle und das Paket **hinzugefügt, ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**und **ColumnGuideCommandsPackage.vsct**hinzugefügt. Im folgenden Abschnitt ersetzen Sie den Inhalt der ersten und letzten Dateien, um die Befehle zu definieren und zu implementieren.

## <a name="set-up-the-text-view-creation-listener"></a>Einrichten des Textansichtserstellungslisteners
Öffnen *Sie ColumnGuideAdornmentTextViewCreationListener.cs* im Editor. Dieser Code implementiert einen Handler für jedes Mal, wenn Visual Studio Textansichten erstellt. Es gibt Attribute, die steuern, wann der Handler aufgerufen wird, abhängig von den Merkmalen der Ansicht.

Der Code muss auch eine Verzierungsebene deklarieren. Wenn der Editor Ansichten aktualisiert, ruft er die Verzierungs-Layer für die Ansicht ab und ruft daraus die Verzierungselemente ab. Sie können die Reihenfolge des Layers relativ zu anderen Mitattributen deklarieren. Ersetzen Sie die folgende Zeile:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

mit diesen beiden Zeilen:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Die Zeile, die Sie ersetzt haben, befindet sich in einer Gruppe von Attributen, die einen Verzierungs-Layer deklarieren. Die erste Zeile, die Sie geändert haben, ändert sich nur dort, wo die Spaltenführungen angezeigt werden. Wenn Sie die Zeilen "vor" dem Text in der Ansicht zeichnen, wird er hinter oder unter dem Text angezeigt. In der zweiten Zeile wird deklariert, dass die Spaltenführungsverzierungen auf Textentitäten anwendbar sind, die zu Ihrem Begriff eines Dokuments passen, Sie jedoch die Verzierung z. B. für bearbeitbaren Text deklarieren könnten. Weitere Informationen finden Sie in [den Sprachdienst- und Editorerweiterungspunkten](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Implementieren des Einstellungs-Managers
Ersetzen Sie den Inhalt der *GuidesSettingsManager.cs* durch den folgenden Code (nachfolgend unten):

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

Der größte Teil dieses Codes erstellt und analysiert\<das Einstellungsformat: "RGB( int\<>, int\<>, int>) \<int>, \<int>, ...".  Die ganzzahligen Dateien am Ende sind die einbasierten Spalten, in denen Spaltenführungslinien angezeigt werden sollen. Die Spaltenführungserweiterung erfasst alle Einstellungen in einer einzigen Einstellungswertzeichenfolge.

Es gibt einige Teile des Codes, die hervorgehoben werden sollten. Die folgende Codezeile ruft den verwalteten Visual Studio-Wrapper für den Einstellungsspeicher ab. In den meisten Teilen wird dies über die Windows-Registrierung abstrahiert, aber diese API ist unabhängig vom Speichermechanismus.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Der Visual Studio-Einstellungsspeicher verwendet einen Kategoriebezeichner und einen Einstellungsbezeichner, um alle Einstellungen eindeutig zu identifizieren:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Sie müssen nicht `"Text Editor"` als Kategoriename verwendet werden. Sie können alles auswählen, was Sie mögen.

Die ersten Funktionen sind die Einstiegspunkte, um Einstellungen zu ändern. Sie überprüfen einschränkungen auf hoher Ebene, wie die maximale Anzahl der zulässigen Hilfslinien.  Dann rufen `WriteSettings`sie auf , die eine Einstellungszeichenfolge erstellt und die Eigenschaft `GuideLinesConfiguration`festlegt. Durch Festlegen dieser Eigenschaft wird der Einstellungswert `SettingsChanged` im Visual Studio-Einstellungsspeicher gespeichert und das Ereignis ausgelöst, um alle Objekte zu aktualisieren, die `ColumnGuideAdornment` jeweils einer Textansicht zugeordnet sind.

Es gibt einige Einstiegspunktfunktionen, `CanAddGuideline`z. B. , die verwendet werden, um Befehle zu implementieren, die Einstellungen ändern. Wenn Visual Studio Menüs anzeigt, werden Befehlsimplementierungen abgefragt, um festzustellen, ob der Befehl derzeit aktiviert ist, wie sein Name lautet usw.  Im Folgenden erfahren Sie, wie Sie diese Einstiegspunkte für die Befehlsimplementierungen verbinden. Weitere Informationen zu Befehlen finden Sie unter Erweitern von [Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementieren der ColumnGuideAdornment-Klasse
Die `ColumnGuideAdornment` Klasse wird für jede Textansicht instanziiert, die Verzierungen haben kann. Diese Klasse überwacht Ereignisse, bei der die Ansicht geändert oder Einstellungen geändert werden, und die Spaltenleitfäden zum Aktualisieren oder Neuzeichnen werden bei Bedarf.

Ersetzen Sie den Inhalt der *ColumnGuideAdornment.cs* durch den folgenden Code (nachfolgend unten):

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

Instanzen dieser Klasse halten <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> an der `Line` zugeordneten und einer Liste von Objekten fest, die in der Ansicht gezeichnet wurden.

Der Konstruktor (aufgerufen ab dem Zeitpunkt, an `ColumnGuideAdornmentTextViewCreationListener` `Line` dem Visual Studio neue Ansichten erstellt) erstellt die Spaltenführungsobjekte.  Der Konstruktor fügt auch `SettingsChanged` Handler für `GuidesSettingsManager`das Ereignis (definiert in ) und die Ansichtsereignisse `LayoutChanged` und `Closed`hinzu.

Das `LayoutChanged` Ereignis wird aufgrund verschiedener Arten von Änderungen in der Ansicht ausgelöst, z. B. beim Erstellen der Ansicht durch Visual Studio. Der `OnViewLayoutChanged` Handler `AddGuidelinesToAdornmentLayer` ruft die Ausführung auf. Der Code `OnViewLayoutChanged` in bestimmt, ob Zeilenpositionen basierend auf Änderungen wie Schriftgrößenänderungen, Ansichtsrinnen, horizontalem Scrollen usw. aktualisiert werden müssen. Der Code `UpdatePositions` in bewirkt, dass Führungslinien zwischen Zeichen oder kurz nach der Textspalte gezeichnet werden, die sich im angegebenen Zeichenversatz in der Textzeile befindet.

Immer wenn `SettingsChanged` Einstellungen ändern, erstellt `Line` die Funktion nur alle Objekte mit den neuen Einstellungen neu. Nach dem Festlegen der Zeilenpositionen entfernt `Line` der `ColumnGuideAdornment` Code alle vorherigen Objekte aus der Verzierungsebene und fügt die neuen hinzu.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definieren der Befehle, Menüs und Menüplatzierungen
Es kann eine Menge sein, Befehle und Menüs zu deklarieren, Befehlsgruppen oder Menüs in verschiedenen anderen Menüs zu platzieren und Befehlshandler einzubinden. In dieser exemplarischen Vorgehensweise wird erläutert, wie Befehle in dieser Erweiterung funktionieren, aber für tiefere Informationen finden Sie weitere Informationen unter Erweitern von [Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Einführung in den Code
Die Erweiterung Spaltenführungslinien zeigt das Deklarieren einer Gruppe von Befehlen an, die zusammengehören (Spalte hinzufügen, Spalte entfernen, Linienfarbe ändern) und diese Gruppe dann in einem Untermenü des Kontextmenüs des Editors platzieren.  Die Erweiterung Spaltenführungslinien fügt die Befehle auch zum Hauptmenü **Bearbeiten** hinzu, hält sie jedoch unsichtbar, wird unten als allgemeines Muster besprochen.

Die Befehlsimplementierung besteht aus drei Teilen: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct und ColumnGuideCommands.cs. Der von den Vorlagen generierte Code setzt einen Befehl im Menü **Extras** ab, der ein Dialogfeld als Implementierung einstellt. Sie können sich ansehen, wie dies in den *Dateien .vsct* und *ColumnGuideCommands.cs* implementiert wird, da es einfach ist. Sie ersetzen den Code in diesen Dateien unten.

Der Paketcode enthält Boilerplate-Deklarationen, die für Visual Studio erforderlich sind, um zu ermitteln, dass die Erweiterung Befehle bietet, und um zu finden, wo die Befehle platziert werden sollen. Wenn das Paket initialisiert wird, instanziiert es die Befehlsimplementierungsklasse. Weitere Informationen zu Paketen, die sich auf Befehle beziehen, finden Sie unter Erweitern von [Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Ein allgemeines Befehlsmuster
Die Befehle in der Erweiterung Spaltenhilfslinien sind ein Beispiel für ein sehr häufiges Muster in Visual Studio. Sie setzen verwandte Befehle in eine Gruppe, und Sie setzen`<CommandFlag>CommandWellOnly</CommandFlag>`diese Gruppe in ein Hauptmenü, oft mit " , um den Befehl unsichtbar zu machen.  Wenn Sie Befehle in die Hauptmenüs eingeben (z. B. **Bearbeiten**), erhalten Sie nette Namen (z. B. **Edit.AddColumnGuide**), die nützlich sind, um Befehle beim erneuten Zuweisen von Schlüsselbindungen in **Tools-Optionen**zu finden. Es ist auch nützlich, um den Abschluss zu erhalten, wenn Befehle aus dem **Befehlsfenster**aufrufen.

Anschließend fügen Sie die Befehlsgruppe zu Kontextmenüs oder Untermenüs hinzu, in denen Sie erwarten, dass der Benutzer die Befehle verwendet. Visual Studio `CommandWellOnly` behandelt als Unsichtbarkeitsflag nur für Hauptmenüs. Wenn Sie dieselbe Befehlsgruppe in einem Kontextmenü oder Untermenü platzieren, sind die Befehle sichtbar.

Als Teil des allgemeinen Musters erstellt die Erweiterung Spaltenführungslinien eine zweite Gruppe, die ein einzelnes Untermenü enthält. Das Untermenü wiederum enthält die erste Gruppe mit den vierspaltigen Führungsbefehlen. Die zweite Gruppe, die das Untermenü enthält, ist das wiederverwendbare Asset, das Sie in verschiedenen Kontextmenüs platzieren, wodurch ein Untermenü in diesen Kontextmenüs platziert wird.

### <a name="the-vsct-file"></a>Die .vsct-Datei
Die *.vsct-Datei* deklariert die Befehle und wo sie gehen, zusammen mit Symbolen und so weiter. Ersetzen Sie den Inhalt der *.vsct-Datei* durch den folgenden Code (nachfolgend unten):

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

**GUIDS**. Damit Visual Studio Ihre Befehlshandler finden und aufruft, müssen Sie sicherstellen, dass die in der *ColumnGuideCommandsPackage.cs-Datei* deklarierte Paket-GUID (generiert aus der Projektelementvorlage) mit der in der *.vsct-Datei* deklarierten Paket-GUID übereinstimmt (von oben kopiert). Wenn Sie diesen Beispielcode wiederverwenden, sollten Sie sicherstellen, dass Sie über eine andere GUID verfügen, damit Sie keinen Konflikt mit anderen Personen haben, die diesen Code möglicherweise kopiert haben.

Suchen Sie diese Zeile in *ColumnGuideCommandsPackage.cs* und kopieren Sie die GUID zwischen den Anführungszeichen:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Fügen Sie dann die GUID in die *.vsct-Datei* `Symbols` ein, damit Sie die folgende Zeile in Ihren Deklarationen haben:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Die GUIDs für den Befehlssatz und die Bitmap-Image-Datei sollten auch für Ihre Erweiterungen eindeutig sein:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Sie müssen jedoch den Befehlssatz und die Bitmap-Bild-GUIDs in dieser exemplarischen Vorgehensweise nicht ändern, um den Code zum Funktionieren zu bringen. Der Befehlssatz GUID muss mit der Deklaration in der *ColumnGuideCommands.cs* Datei übereinstimmen, aber Sie ersetzen auch den Inhalt dieser Datei. Daher stimmen die GUIDs überein.

Andere GUIDs in der *.vsct-Datei* identifizieren bereits vorhandene Menüs, denen die Spaltenführungsbefehle hinzugefügt werden, sodass sie sich nie ändern.

**Dateiabschnitte**. Der *.vsct* hat drei äußere Abschnitte: Befehle, Platzierungen und Symbole. Der Befehlsabschnitt definiert Befehlsgruppen, Menüs, Schaltflächen oder Menüelemente und Bitmaps für Symbole. Im Abschnitt Platzierungen wird erklärt, wo Gruppen in Menüs oder zusätzliche Platzierungen auf bereits vorhandenen Menüs platziert werden. Der Abschnitt Symbole deklariert Bezeichner, die an anderer Stelle in der *.vsct-Datei* verwendet werden, wodurch der *.vsct-Code* besser lesbar ist, als überall GUIDs und Hex-Nummern zu haben.

**Befehlsabschnitt, Gruppendefinitionen**. Der Befehlsabschnitt definiert zuerst Befehlsgruppen. Befehlsgruppen sind Befehle, die Sie in Menüs mit leichten grauen Linien sehen, die die Gruppen trennen. Eine Gruppe kann auch ein gesamtes Untermenü füllen, wie in diesem Beispiel, und in diesem Fall werden die grauen Trennlinien nicht angezeigt. Die *.vsct-Dateien* deklarieren zwei Gruppen, die `GuidesMenuItemsGroup` dem `IDM_VS_MENU_EDIT` Menü **"Hauptbearbeitung"** und dem `GuidesContextMenuGroup` ,,das" `IDM_VS_CTXT_CODEWIN` (kontextmenü des Code-Editors) übergeordnet ist.

Die zweite Gruppenerklärung `0x0600` hat eine Priorität:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Die Idee ist, die Spaltenführungslinien unter dem Menü am Ende eines beliebigen Kontextmenüs zu setzen, dem Sie die Untermenügruppe hinzufügen. Sie sollten jedoch nicht davon ausgehen, dass Sie es am besten wissen, und das Untermenü zwingen, immer letzter zu sein, indem Sie die Priorität von `0xFFFF`verwenden. Sie müssen mit der Zahl experimentieren, um zu sehen, wo sich Ihr Untermenü in den Kontextmenüs befindet, in denen Sie es platzieren. In diesem `0x0600` Fall ist hoch genug, um es am Ende der Menüs so weit wie Sie sehen können, aber es lässt Raum für jemand anderen, um ihre Erweiterung zu entwerfen, um niedriger als die Spaltenführungen Erweiterung zu sein, wenn dies wünschenswert ist.

**Befehlsabschnitt, Menüdefinition**. Als Nächstes definiert der Befehlsabschnitt das Untermenü `GuidesSubMenu`, das dem `GuidesContextMenuGroup`übergeordnet ist. Die `GuidesContextMenuGroup` ist die Gruppe, die Sie allen relevanten Kontextmenüs hinzufügen. Im Abschnitt Platzierungen platziert der Code die Gruppe mit den vierspaltigen Führungsbefehlen in diesem Untermenü.

**Befehlsabschnitt, Schaltflächendefinitionen**. Der Befehlsabschnitt definiert dann die Menüelemente oder Schaltflächen, die die Befehle für vier Spaltenführungslinien sind. `CommandWellOnly`, wie oben besprochen, bedeutet, dass die Befehle unsichtbar sind, wenn sie in einem Hauptmenü platziert werden. Zwei der Menüpunkt-Schaltflächendedede (Leitfaden hinzufügen `AllowParams` und Leitfaden entfernen) haben auch ein Flag:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Dieses Flag ermöglicht neben Hauptmenüplatzierungen den Befehl, Argumente zu empfangen, wenn Visual Studio den Befehlshandler aufruft.  Wenn der Benutzer den Befehl über das Befehlsfenster ausführt, wird das Argument an den Befehlshandler in den Ereignisargumenten übergeben.

**Befehlsabschnitte, Bitmaps-Definitionen**. Schließlich werden im Befehlsabschnitt die Bitmaps oder Symbole deklariert, die für die Befehle verwendet werden. Dieser Abschnitt ist eine einfache Deklaration, die die Projektressource identifiziert und ein einzige Indizes verwendeter Symbole auflistet. Der Symbolabschnitt der *.vsct-Datei* deklariert die Werte der Bezeichner, die als Indizes verwendet werden. In dieser exemplarischen Vorgehensweise wird der Bitmap-Strip verwendet, der mit der benutzerdefinierten Befehlselementvorlage bereitgestellt wird, die dem Projekt hinzugefügt wurde.

**Abschnitt Platzierungen**. Nach dem Befehlsabschnitt wird der Abschnitt Platzierungen angezeigt. Die erste ist, wo der Code die erste oben besprochene Gruppe hinzufügt, die die vierspaltenden Führungsbefehle enthält, zum Untermenü, in dem die Befehle angezeigt werden:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Alle anderen Platzierungen fügen `GuidesContextMenuGroup` die (die die enthält ) `GuidesSubMenu`zu anderen Editor-Kontextmenüs hinzu. Als der Code `GuidesContextMenuGroup`die deklarierte, wurde er im Kontextmenü des Codeeditors übergeordnet. Aus diesem Grund wird keine Platzierung für das Kontextmenü des Code-Editors angezeigt.

**Symbole Abschnitt**. Wie oben erwähnt, deklariert der Symbolabschnitt Bezeichner, die an anderer Stelle in der *.vsct-Datei* verwendet werden, was den *.vsct-Code* lesbarer macht, als GUIDs und Hex-Nummern überall zu haben. Die wichtigsten Punkte in diesem Abschnitt sind, dass die Paket-GUID mit der Deklaration in der Paketklasse übereinstimmen muss. Und der Befehlssatz GUID muss mit der Deklaration in der Befehlsimplementierungsklasse übereinstimmen.

## <a name="implement-the-commands"></a>Implementieren der Befehle
Die *ColumnGuideCommands.cs-Datei* implementiert die Befehle und schließt die Handler ein. Wenn Visual Studio das Paket lädt und initialisiert, `Initialize` ruft das Paket wiederum die Befehlsimplementierungsklasse auf. Die Befehlsinitialisierung instanziiert einfach die Klasse, und der Konstruktor schließt alle Befehlshandler an.

Ersetzen Sie den Inhalt der *ColumnGuideCommands.cs* Datei durch den folgenden Code (nachfolgend unten):

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

**Korrekturreferenzen**. An dieser Stelle fehlt ein Verweis. Drücken Sie die rechte Zeigertaste auf dem Verweisknoten im Projektmappen-Explorer. Wählen Sie den Befehl **Hinzufügen ...** aus. Das Dialogfeld **Referenz hinzufügen** verfügt über ein Suchfeld in der oberen rechten Ecke. Geben Sie "Editor" (ohne doppelte Anführungszeichen) ein. Wählen Sie das Element **Microsoft.VisualStudio.Editor** (Sie müssen das Kontrollkästchen links neben dem Element aktivieren, nicht nur das Element auswählen) und wählen Sie **OK,** um den Verweis hinzuzufügen.

**Initialisierung**.  Wenn die Paketklasse initialisiert `Initialize` wird, ruft sie die Befehlsimplementierungsklasse auf. Die `ColumnGuideCommands` Initialisierung instanziiert die Klasse und speichert die Klasseninstanz und den Paketverweis in Klassenmembern.

Sehen wir uns einen der Befehlshandler-Hook-Ups des Klassenkonstruktors an:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Sie erstellen `OleMenuCommand`eine . Visual Studio verwendet das Microsoft Office-Befehlssystem. Die wichtigsten Argumente beim Instanziieren von a `OleMenuCommand` ist`AddColumnGuideExecuted`die Funktion, die den Befehl ( )`AddColumnGuideBeforeQueryStatus`implementiert, die Funktion, die aufruft, wenn Visual Studio ein Menü mit dem Befehl ( ) und der Befehls-ID anzeigt. Visual Studio ruft die Abfragestatusfunktion auf, bevor ein Befehl in einem Menü angezeigt wird, sodass der Befehl sich für eine bestimmte Anzeige des Menüs unsichtbar oder ausgegraut machen kann (z. B. Deaktivierung von **Kopieren,** wenn keine Auswahl vorhanden ist), das Symbol ändert oder sogar seinen Namen ändert (z. B. von Something hinzufügen, um etwas zu entfernen), und so weiter. Die Befehls-ID muss mit einer Befehls-ID übereinstimmen, die in der *.vsct-Datei* deklariert ist. Die Zeichenfolgen für den Befehlssatz und die Spaltenhilfslinien add-Befehl müssen zwischen der *.vsct-Datei* und dem *ColumnGuideCommands.cs*übereinstimmen.

Die folgende Zeile bietet Unterstützung für den Aufruf des Befehls über das Befehlsfenster (unten):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Abfragestatus**. Der Abfragestatus `AddColumnGuideBeforeQueryStatus` `RemoveColumnGuideBeforeQueryStatus` funktioniert und überprüft einige Einstellungen (z. B. max Anzahl von Hilfslinien oder max Spalte) oder wenn es eine Spaltenführung zum Entfernen gibt. Sie aktivieren die Befehle, wenn die Bedingungen stimmen.  Abfragestatusfunktionen müssen effizient sein, da sie jedes Mal ausgeführt werden, wenn Visual Studio ein Menü und für jeden Befehl im Menü anzeigt.

 **AddColumnGuideExecuted-Funktion**. Der interessante Teil des Hinzufügens eines Leitfadens ist das Herausfinden der aktuellen Editoransicht und Der einpflegenden Position.  Zuerst ruft diese `GetApplicableColumn`Funktion auf, die überprüft, ob ein vom Benutzer bereitgestelltes Argument in den Ereignisargumenten des Befehlshandlers vorhanden ist, und wenn keine vorhanden sind, überprüft die Funktion die Ansicht des Editors:

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

`GetCurrentEditorColumn`muss ein wenig graben, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> um einen Blick auf den Code zu erhalten.  Wenn Sie `GetActiveTextView`durch `GetActiveView`, `GetTextViewFromVsTextView`und , nachverfolgen, können Sie sehen, wie Sie dies tun. Der folgende Code ist der relevante Code abstrahiert, beginnend mit der aktuellen Auswahl, dann abrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>sie den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> Frame der Auswahl, dann abrufen Sie die DocView des Frames als , dann abrufen Sie eine aus der IVsTextView, dann abrufen Sie einen Ansichtshost, und schließlich die IWpfTextView:

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

Sobald Sie eine IWpfTextView haben, können Sie die Spalte abrufen, in der sich die Einserstelle befindet:

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

Mit der aktuellen Spalte in der Hand, auf die der Benutzer geklickt hat, ruft der Code nur den Einstellungs-Manager auf, um die Spalte hinzuzufügen oder zu entfernen. Der Einstellungs-Manager löst `ColumnGuideAdornment` das Ereignis aus, auf das alle Objekte lauschen. Wenn das Ereignis ausgelöst wird, aktualisieren diese Objekte ihre zugehörigen Textansichten mit neuen Spaltenführungseinstellungen.

## <a name="invoke-command-from-the-command-window"></a>Aufrufen des Befehls aus dem Befehlsfenster
Das Beispiel für Spaltenhilfslinien ermöglicht es Benutzern, zwei Befehle aus dem Befehlsfenster als eine Form der Erweiterbarkeit aufzurufen. Wenn Sie den Befehl **"Anzeigen &#124; andere Windows &#124; Befehlsfenster"** verwenden, wird das Befehlsfenster angezeigt. Sie können mit dem Befehlsfenster interagieren, indem Sie "bearbeiten") eingeben, und mit der Ausführung des Befehlsnamens und der Bereitstellung des Arguments 120 haben Sie folgendes Ergebnis:

```csharp
> Edit.AddColumnGuide 120
>
```

Die Teile des Beispiels, die dieses Verhalten aktivieren, befinden `ColumnGuideCommands` sich in den .vsct-Dateideklarationen, dem Klassenkonstruktor beim Verbinden von Befehlshandlern und den Befehlshandlerimplementierungen, die Ereignisargumente überprüfen. *.vsct*

Sie haben`<CommandFlag>CommandWellOnly</CommandFlag>`" in der *.vsct-Datei* sowie Platzierungen im Hauptmenü **Bearbeiten** gesehen, obwohl die Befehle nicht in der Menü-Benutzeroberfläche **zum Bearbeiten** angezeigt werden. Wenn sie im Hauptmenü **Bearbeiten** angezeigt werden, erhalten sie Namen wie **Edit.AddColumnGuide**. Die Befehlsgruppendeklaration, die die vier Befehle enthält, platziert die Gruppe direkt im Menü **Bearbeiten:**

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Der Schaltflächenabschnitt erklärte `CommandWellOnly` später die Befehle, um sie `AllowParams`im Hauptmenü unsichtbar zu halten, und deklarierte sie mit:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Sie haben gesehen, dass der `ColumnGuideCommands` Befehlshandler den Code im Klassenkonstruktor angeschlossen hat, der eine Beschreibung des zulässigen Parameters bereitgestellt hat:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Sie haben `GetApplicableColumn` die `OleMenuCmdEventArgs` Funktion auf einen Wert überprüft, bevor Sie die Ansicht des Editors auf eine aktuelle Spalte überprüft haben:

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

## <a name="try-your-extension"></a>Versuchen Sie Ihre Erweiterung
Sie können jetzt **F5** drücken, um Ihre Spaltenführungserweiterung auszuführen. Öffnen Sie eine Textdatei, und verwenden Sie das Kontextmenü des Editors, um Hilfslinien hinzuzufügen, sie zu entfernen und ihre Farbe zu ändern. Klicken Sie in den Text (nicht Leerzeichen am Ende der Zeile übergeben), um eine Spaltenführung hinzuzufügen, oder der Editor fügt sie der letzten Spalte in der Zeile hinzu. Wenn Sie das Befehlsfenster verwenden und die Befehle mit einem Argument aufrufen, können Sie überall Spaltenführungslinien hinzufügen.

Wenn Sie verschiedene Befehlsplatzierungen ausprobieren, Namen ändern, Symbole ändern usw. und Probleme mit Visual Studio haben, in denen der neueste Code in menüs angezeigt wird, können Sie die experimentelle Struktur zurücksetzen, in der Sie debuggen. Schalten Sie das **Windows-Startmenü** auf und geben Sie "Reset" ein. Suchen und führen Sie den Befehl **Zurücksetzen der nächsten Visual Studio-Experimentalinstanz**aus. Dieser Befehl bereinigt die experimentelle Registrierungsstruktur aller Erweiterungskomponenten. Es bereinigt keine Einstellungen aus Komponenten, sodass alle Leitfäden, die Sie beim Herunterfahren der experimentellen Struktur von Visual Studio hatten, immer noch vorhanden sind, wenn Ihr Code den Einstellungsspeicher beim nächsten Start liest.

## <a name="finished-code-project"></a>Fertiges Codeprojekt
In Kürze wird es ein GitHub-Projekt mit Visual Studio-Extensibilitätsbeispielen geben, und das abgeschlossene Projekt wird vorhanden sein. Dieser Artikel wird aktualisiert, um dort zu zeigen, wenn dies geschieht. Das abgeschlossene Beispielprojekt kann unterschiedliche GUIDs haben und einen anderen Bitmaps-Streifen für die Befehlssymbole haben.

Mit dieser Visual Studio[Gallery-Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)können Sie eine Version des Column Guides-Features ausprobieren.

## <a name="see-also"></a>Weitere Informationen
- [Innerhalb des Editors](../extensibility/inside-the-editor.md)
- [Erweitern der Editor- und Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)
- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)
- [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)
