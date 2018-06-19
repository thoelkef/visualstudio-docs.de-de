---
title: Erstellen einer Ansicht Randsteuerelement, Befehle und Einstellungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 57a7696eae0da92d88babf64c580a4767775dffd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148193"
---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Exemplarische Vorgehensweise: Erstellen einer Ansicht Randsteuerelement, Befehle und Einstellungen (Spalte Handbücher)
Sie können die Visual Studio-Text oder den Code-Editor mit Befehlen und Anzeigen von Effekten erweitern.  In diesem Thema wird gezeigt, wie eine beliebte Erweiterungsfunktion Spalte Handbücher Einstieg.  Spalte Handbücher werden visuell Licht auf das Text-Editor-Ansicht zur einfacheren Verwaltung des Codes: auf bestimmte Spaltenbreite gezeichneten Linien verwendet.  Speziell formatierte Code kann für die Beispiele sind wichtig sein, in Blogbeiträgen,-Dokumenten enthalten oder Fehlerberichte.  
  
 In dieser exemplarischen Vorgehensweise führen Sie folgende Aktionen ausführen:  
  
-   Erstellen Sie ein VSIX-Projekt  
  
-   Fügen Sie eine Editor-Ansicht Zusatzelement (adornment)  
  
-   Hinzufügen von Unterstützung für das Speichern und Abrufen von Einstellungen (wobei zum Zeichnen Spalten- und ihre Farbe)  
  
-   Hinzufügen von Befehlen (Spalte Handbücher hinzufügen/entfernen, ändern Sie ihre Farbe)  
  
-   Platzieren Sie die Befehle im Menü Bearbeiten, und Text-Dokument-Kontextmenüs  
  
-   Hinzufügen von Unterstützung für die Befehle an der Visual Studio-Befehlsfenster aufrufen  
  
 Sie können versuchen, eine Version von der Funktion "Spalte Handbücher" mit diesem Visual Studio Gallery[Erweiterung](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
 **Hinweis**: in dieser exemplarischen Vorgehensweise fügen Sie Sie viel Code in einige Dateien, die visual Studio-Erweiterung Vorlagen generiert werden, aber in dieser exemplarischen Vorgehensweise wird bald finden Sie in einer vollständigen Lösung auf Github mit anderen erweiterungsbeispiele.  Der vollständige Code ist etwas anders, da sie echte Befehlssymbole anstatt Generictemplate Symbole hat.  
  
## <a name="getting-started"></a>Erste Schritte  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="setting-up-the-solution"></a>Die Lösung einrichten  
 Sie werden zuerst ein VSIX-Projekt ein Editor-Ansicht Zusatzelement (adornment) hinzufügen und fügen Sie einen Befehl (bei dem ein VSPackage zum Besitzer des Befehls fügt) hinzu.  Die grundlegende Architektur lautet wie folgt:  
  
-   Sie haben einen Text-Ansicht-Erstellung-Listener, der erstellt ein `ColumnGuideAdornment` Objekt pro Ansicht.  Dieses Objekt überwacht wird, für Ereignisse im Zusammenhang mit der Ansicht ändern oder Einstellungen ändern, aktualisieren oder erneutes Spalte führt nach Bedarf.  
  
-   Es wird eine `GuidesSettingsManager` lesen und Schreiben von aus dem Speicher der Visual Studio-Einstellungen, die verarbeitet.  Einstellungs-Manager bietet auch Vorgänge zum Aktualisieren der Einstellungen, die die Benutzerbefehle unterstützen (Spalte hinzufügen, entfernen Sie die Spalte und Farbe ändern).  
  
-   Es ist ein VSIP-Paket, das ist erforderlich, wenn Sie Benutzerbefehle haben allerdings handelt es sich einfach Standardcode, der die Befehle Implementierungsobjekt initialisiert.  
  
-   Es ist ein `ColumnGuideCommands` -Objekt, das die Benutzerbefehle implementiert und bindet die Befehlshandler für Befehle, die in der VSCT-Datei deklariert.  
  
 **VSIX**.  Verwendung **Datei &#124; neu...**  Befehl aus, um ein Projekt zu erstellen.  Wählen Sie die Erweiterbarkeit Knoten unter c# im linken Navigationsbereich, und wählen Sie **VSIX-Projekt** im rechten Bereich.  Geben Sie den Namen ColumnGuides, und wählen Sie **OK** zum Erstellen des Projekts.  
  
 **Anzeigen von Randsteuerelement**.  Drücken Sie die Zeiger nach rechts auf den Projektknoten im Projektmappen-Explorer.  Wählen Sie die **hinzufügen &#124; neues Element...**  Befehl aus, um ein neues Ansicht Randsteuerelement Element hinzuzufügen.  Wählen Sie **Erweiterbarkeit &#124; Editor** im linken Navigationsbereich, und wählen Sie **Editor Viewport Randsteuerelement** im rechten Bereich.  Geben Sie den Namen ColumnGuideAdornment als Name des Elements, und wählen Sie **hinzufügen** hinzufügen.  
  
 Sie sehen, dass diese Elementvorlage zwei Dateien dem Projekt (als auch Verweise und usw.) hinzugefügt: ColumnGuideAdornment.cs und ColumnGuideAdornmentTextViewCreationListener.cs.  Die Vorlagen Zeichnen nur eine violette Rechteck für die Sicht.  Im folgenden Sie ändern eine Reihe von Zeilen in der Ansicht Erstellung-Listener und Ersetzen Sie den Inhalt des ColumnGuideAdornment.cs.  
  
 **Befehle**.  Drücken Sie die Zeiger nach rechts auf den Projektknoten im Projektmappen-Explorer.  Wählen Sie die **hinzufügen &#124; neues Element...**  Befehl aus, um ein neues Ansicht Randsteuerelement Element hinzuzufügen.  Wählen Sie **Erweiterbarkeit &#124; VSPackage** im linken Navigationsbereich, und wählen Sie **benutzerdefinierte Befehl** im rechten Bereich.  Geben Sie den Namen ColumnGuideCommands als Name des Elements, und wählen Sie **hinzufügen** hinzufügen.  ColumnGuideCommands.cs ColumnGuideCommandsPackage.cs und ColumnGuideCommandsPackage.vsct sowie mehrere Verweise hinzugefügt hinzufügen, die Befehle und das Paket.  Im folgenden ersetzen Sie den Inhalt der ersten und letzten Dateien definieren und implementieren die Befehle.  
  
## <a name="setting-up-the-text-view-creation-listener"></a>Der Text anzeigen Erstellung Listener einrichten  
 ColumnGuideAdornmentTextViewCreationListener.cs im Editor zu öffnen.  Dieser Code implementiert einen Handler für bei jedem Text-Ansichten von Visual Studio erstellt.  Attribute, mit denen gesteuert wird, wenn der Handler aufgerufen wird, abhängig von Eigenschaften der Sicht sind vorhanden.  
  
 Der Code muss auch eine Randsteuerelement-Ebene deklariert.  Wenn der Editor Sichten aktualisiert, ruft die Randsteuerelement Ebenen für die Ansicht und ruft aus, die die Randsteuerelement-Elemente.  Sie können deklarieren, die Reihenfolge der Ebene relativ zu anderen mit Attributen.  Ersetzen Sie die folgende Zeile:  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 Durch diese zwei Zeilen:  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 Die Zeile an, die Sie ersetzt wird eine Gruppe von Attributen, die eine Randsteuerelement-Ebene zu deklarieren.   Die erste Zeile haben Sie nur Änderungen, die Anzeigeposition der Führungslinien Spalte geändert.  Zeichnen von Linien "vor" der Text in der Ansicht bedeutet, dass sie hinter oder unter dem Text angezeigt werden.  Die zweite Zeile deklariert, dass die Spalte Handbuch Zusatzelemente gelten für Text-Entitäten, die Ihre Idee eines Dokuments entsprechen, aber Sie das Zusatzelement z. B., um nur die Arbeit für den Text bearbeitet werden deklarieren konnte.  Es sind weitere Informationen in [Sprachdienst und Erweiterungspunkten-Editor](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>Implementieren der Einstellungs-Manager  
 Ersetzen Sie den Inhalt der GuidesSettingsManager.cs durch den folgenden Code (siehe unten):  
  
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
  
 Die meisten dieser Code einfach erstellt und analysiert die Settings-Format: "RGB (\<Int >,\<Int >,\<Int >) \<Int >, \<Int >,...".  Die ganzen Zahlen am Ende entsprechen Spalten den einsbasierten Spalte Handbücher werden soll.  Die Spalte Handbücher Erweiterung erfasst alle Einstellungen in eine einzelne Einstellung Wertzeichenfolge.  
  
 Es gibt einige Teile des Codes zu markieren.  Die folgende Codezeile Ruft die Visual Studio-verwalteten Wrapper für die Speicherung der Einstellungen.  Meistens, dies über die Windows-Registrierung abstrahiert, aber diese API ist unabhängig von der Speichermechanismus.  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Der Visual Studio-Einstellungen-Speicher verwendet eine Kategorie-ID und einer Einstellung-ID zur eindeutigen Identifizierung der alle Einstellungen:  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 Sie müssen keine verwenden `"Text Editor"` als Kategorie Namen, und Sie können auswählen, beliebig.  
  
 Die erste einige Funktionen sind Einstiegspunkte Einstellungen zu ändern.  Prüfen auf hoher Ebene Einschränkungen wie die maximale Anzahl von Führungslinien zulässig.  Anschließend sie rufen `WriteSettings` die verfasst einer einstellungszeichenfolge und legt die Eigenschaft `GuideLinesConfiguration`.  Durch Festlegen dieser Eigenschaft speichert den Einstellungswert der Visual Studio-Einstellungen-Store und löst die `SettingsChanged` Ereignis alle Aktualisieren der `ColumnGuideAdornment` Objekte jeweils eine Textansicht zugeordnet.  
  
 Gibt es eine Reihe von Eintrag Point-Funktionen, wie z. B. `CanAddGuideline`, werden verwendet, um Befehle zu implementieren, die Einstellungen zu ändern.  Wenn Visual Studio Menüs angezeigt wird, fragt sie ab usw. Befehl-Implementierungen, um festzustellen, ob der Befehl derzeit aktiviert ist, was ist der Name.  Im folgenden sehen Sie, wie Sie diese Einstiegspunkte für den Befehl Implementierungen einbinden.  Finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md) für Weitere Informationen zu Befehlen.  
  
## <a name="implementing-the-columnguideadornment-class"></a>Implementieren die ColumnGuideAdornment-Klasse  
 Die `ColumnGuideAdornment` Klasse für jede Textansicht Zusatzelemente denen instanziiert wird.  Diese Klasse überwacht Ereignisse im Zusammenhang mit der Ansicht ändern oder Einstellungen ändern, aktualisieren oder erneutes Spalte führt nach Bedarf.  
  
 Ersetzen Sie den Inhalt der ColumnGuideAdornment.cs durch den folgenden Code (siehe unten):  
  
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
  
 Instanzen dieser Klasse daran festhalten zugeordneten <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> und eine Liste der `Line` Objekte, die für die Sicht gezeichnet.  
  
 Der Konstruktor (aufgerufen `ColumnGuideAdornmentTextViewCreationListener` bei Visual Studio erstellt neue Ansichten) im Handbuch für die Spalte erstellt `Line` Objekte.  Der Konstruktor fügt auch Handler für das `SettingsChanged` Ereignis (definiert `GuidesSettingsManager`) und das Anzeigen von Ereignissen `LayoutChanged` und `Closed`.  
  
 Die `LayoutChanged` Ereignis ausgelöst wird, aufgrund der verschiedenen Arten von Änderungen in der Ansicht z. B., wenn Visual Studio die Ansicht erstellt.  Die `OnViewLayoutChanged` Ereignishandler ruft `AddGuidelinesToAdornmentLayer` ausgeführt.  Der Code in `OnViewLayoutChanged` bestimmt, ob die Zeile Positionen basierend auf Änderungen wie z. B. Schriftgrad ändert sich, Ansicht Bundstege horizontalen Bildlauf und So weiter aktualisiert werden muss.  Der Code in `UpdatePositions` bewirkt, dass die Führungslinien zwischen Zeichen oder unmittelbar nach der Spalte der Text in der angegebenen Zeichenoffset in der Zeile des Texts gezeichnet werden soll.  
  
 Bei jedem Ändern der Einstellungen der `SettingsChanged` Funktion erstellt alle nur die `Line` Objekte mit die die neuen Einstellungen werden.  Nach dem Festlegen der Zeile Positionen, entfernt der Code alle vorherigen `Line` Objekte aus der `ColumnGuideAdornment` Randsteuerelement-Ebene und fügt neue.  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>Definieren die Befehle, Menüs und Menü Platzierungen  
 Es kann viel zum Deklarieren von Befehlen und Menüs, platzieren Gruppen von Befehlen oder Menüs in verschiedene andere Menüs und Einbinden von Befehlshandler.  In dieser exemplarischen Vorgehensweise werden hervorgehoben, wie die Befehle in dieser Erweiterung, aber eine umfassendere Informationen funktionieren, finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).  
  
### <a name="introduction-to-the-code"></a>Einführung in den Code  
 Die Spalte Handbücher Erweiterung zeigt deklarieren eine Gruppe von Befehlen, die zusammen gehören (Spalte hinzufügen, entfernen Sie die Spalte, ändern Sie die Linienfarbe), und platzieren Sie diese Gruppe in einem Menü Sub des Kontextmenüs des Editors.  Die Spalte Handbücher Erweiterung fügt auch die Befehle für "Main" die **bearbeiten** Menü jedoch werden, werden sie nicht sichtbar ist, als ein allgemeines Muster, die weiter unten erläutert.  
  
 Es gibt drei Teile für die Implementierung der Befehle: ColumnGuideCommandsPackage.cs ColumnGuideCommandsPackage.vsct und ColumnGuideCommands.cs.  Von den Vorlagen generierte Code stellt einen Befehl in der **Tools** als Implementierung ein Dialogfeld angezeigt.  Sie können sich ansehen, die Implementierung in der VSCT und ColumnGuideCommands.cs-Dateien, da es relativ einfach ist.  Sie ersetzen Sie den Code in diesen Dateien, die weiter unten.  
  
 Der Paketcode ist Textbaustein-Deklarationen, die für Visual Studio, um zu ermitteln, dass die Erweiterung bietet, Befehle und platzieren Sie die Befehle erforderlich sind.  Wenn das Paket initialisiert, instanziiert es der Implementierungsklasse des Befehle.  Finden Sie die Befehle, die oben für Weitere Informationen zu Paketen, die im Zusammenhang mit der Befehle zu verknüpfen.  
  
### <a name="a-common-commands-pattern"></a>Ein allgemeines Muster für Befehle  
 Die Befehle in der Spalte Handbücher Erweiterung sind ein Beispiel für ein sehr übliches Muster in Visual Studio.  Eine Gruppe verwandter Befehle gelagerte, und stellen diese Gruppe auf einem Hauptmenü stammt, häufig mit "`<CommandFlag>CommandWellOnly</CommandFlag>`" festgelegt werden, um den Befehl unsichtbar zu machen.  Befehle auf den Hauptmenüs anzuwenden (z. B. **bearbeiten**) auf diese Weise erhalten sie eine nice-Namen (z. B. **Edit.AddColumnGuide**) eignen sich für die Suche nach Befehle beim tastenbindungen in neu zuweisen  **Extras Optionen** und zum Abschluss des Vorgangs abrufen, beim Aufrufen der Befehle aus der **Befehlsfenster**.  
  
 Klicken Sie anschließend die Gruppe von Befehlen zu Kontextmenüs hinzufügen oder sub-Menüs, wo Benutzer mit den Befehlen erwarten.  Visual Studio behandelt `CommandWellOnly` als ein Invisibility-Flag für Hauptmenüs nur.  Wenn Sie die gleiche Gruppe von Befehlen in einem Kontextmenü oder Untermenü platzieren, werden die Befehle angezeigt.  
  
 Im Rahmen des dem allgemeinen Muster erstellt die Spalte Handbücher-Erweiterung eine zweite Gruppe, die ein einzelnes Sub-Menü enthält.  Das Untermenü enthält wiederum die erste Gruppe mit den Befehlen der vier Spalten-Handbuch.  Die zweite Gruppe, die das Untermenü enthält ist wieder verwendbare Medienobjekt, die Sie für verschiedene Kontextmenüs zu sehen, an dem Untermenü auf diese Kontextmenüs setzt.  
  
### <a name="the-vsct-file"></a>Der VSCT-Datei  
 Die VSCT-Datei werden die Befehle und, zusammen mit Symbolen und wo sie deklariert.  Ersetzen Sie den Inhalt der VSCT-Datei durch den folgenden Code (siehe unten):  
  
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
  
 **GUIDS**.  Für Visual Studio die Befehlshandler suchen und diese aufzurufen müssen Sie sicherstellen, dass das Paket, in das GUID in der ColumnGuideCommandsPackage.cs-Datei (aus der Projektelementvorlage generiert) deklariert, das Paket übereinstimmt, das GUID in der VSCT-Datei (von oben kopiert deklariert ).  Wenn Sie diesen Beispielcode erneut verwenden, sollten Sie sicherstellen, dass Sie eine andere GUID verfügen, damit Sie nicht mit anderen Personen in Konflikt stehen, die diesen Code kopiert haben, können.  
  
 Suchen Sie die folgende Zeile in ColumnGuideCommandsPackage.cs, und kopieren Sie die GUID von einschließlich der Anführungszeichen:  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 Fügen Sie die GUID in der VSCT-Datei, sodass Sie die folgende Zeile der `Symbols` Deklarationen:  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 Die GUIDs für den Befehl festgelegt und der Bitmap-Bilddatei sollten für Ihre Erweiterungen eindeutig zu:  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 Sie müssen jedoch nicht zu ändern, den Befehlssatz bitmap-Bild GUIDs in dieser exemplarischen Vorgehensweise, um den Code zu erhalten zu können.  Der Befehlssatz GUID muss die Deklaration in der Datei ColumnGuideCommands.cs überein, aber ersetzen Sie den Inhalt der Datei zu; Daher werden die GUIDs übereinstimmen.  
  
 Andere GUIDs in der VSCT-Datei identifizieren bereits vorhandenen Menüs, die die Spalte Handbuch Befehle hinzugefügt werden, damit sie nie ändern.  
  
 **Abschnitte der Datei**.  Die VSCT besteht aus drei äußeren Abschnitten: Befehle Platzierungen und Symbole.  Befehle im Abschnitt definiert Befehlsgruppen, Menüs, Schaltflächen oder Menüelemente und Bitmaps für Symbole.  Im Abschnitt Platzierungen deklariert an mich bei Gruppen auf Menüs oder zusätzliche Platzierungen auf bereits vorhandene Menüs.  Symbole im Abschnitt deklariert Bezeichner, die an anderer Stelle in der VSCT-Datei, wodurch den VSCT-Code besser lesbar als GUIDs und hexadezimale Ziffern überall verwendet werden.  
  
 **Befehle im Abschnitt, Gruppen oder Definitionen**.  Befehle im Abschnitt definiert zuerst Befehlsgruppen.  Gruppen von Befehle sind Befehle, die in Menüs mit geringfügigen grauen Linien, trennen die Gruppen angezeigt.  Eine Gruppe kann auch eine gesamte Untermenü, wie in diesem Beispiel füllen, und das graue, trennen die Zeilen in diesem Fall nicht angezeigt.  Die VSCT-Dateien deklariert zwei Gruppen der `GuidesMenuItemsGroup` , übergeordnet ist die `IDM_VS_MENU_EDIT` (im Hauptfenster **bearbeiten** Menü) und die `GuidesContextMenuGroup` , übergeordnet ist die `IDM_VS_CTXT_CODEWIN` (der Code-Editor-Kontextmenü).  
  
 Die zweite Gruppendeklaration hat einen `0x0600` Priorität:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 Die Idee ist, die Spalte eingefügt werden soll Untermenü am Ende führt wir alle Kontextmenü, um die Untergruppe Menü hinzu.  Allerdings sollten Sie nicht davon ausgehen Sie am besten kennen, und erzwingen das Untermenü immer im letzten wird mit einer Priorität von `0xFFFF`.  Experimentieren mit dieser Nummer, um festzustellen, wo das Sub-Menü auf die Kontextmenüs liegt, wo Sie es platzieren, müssen.  In diesem Fall `0x0600` ist hoch genug, um am Ende des Menüs zu versetzen, soweit wie Sie sehen, lässt jedoch auch Raum für Personen außerhalb Ihres so entwerfen Sie ihre Erweiterung niedriger ist als die Spalte Handbücher Erweiterung sein, wenn dies wünschenswert ist.  
  
 **Befehle im Abschnitt menüdefinition**.  Als Nächstes im Befehlsabschnitt definiert das Untermenü `GuidesSubMenu`, untergeordnet der `GuidesContextMenuGroup`.  Die `GuidesContextMenuGroup` ist die Gruppe, die wir alle relevanten Kontextmenüs hinzu.  Im Abschnitt Platzierungen platziert der Code die Gruppe mit den vier Spalten Handbuch-Befehlen in diesem Menü Sub.  
  
 **Befehle im Abschnitt, Definitionen Schaltflächen**.  Befehle im Abschnitt definiert die Menüelemente oder Schaltflächen, die vier Spalten sind führt Befehle.  `CommandWellOnly`, weiter oben erläuterten, bedeutet, dass die Befehle sind nicht sichtbar, wenn es auf einem Hauptmenü platziert.  Zwei des Menüelements Schaltfläche Deklarationen (Handbuch hinzufügen und entfernen Sie die Anleitung) haben Sie auch eine `AllowParams` Kennzeichen:  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 Dieses Flag kann zusammen mit mit Hauptmenü Platzierungen, den Befehl aus, um Argumente zu erhalten, wenn Visual Studio Befehlshandler aufruft.  Wenn der Benutzer den Befehl in das Befehlsfenster aufruft, ruft das Argument an Befehlshandler im Ereignis Argumente übergeben.  
  
 **Befehl Abschnitte, Bitmaps Definitionen**.  Schließlich deklariert Befehle im Abschnitt die Bitmaps oder Symbole, die für die Befehle verwendet.  Dies ist eine einfache Deklaration, die identifiziert die Projektressource und 1 basierenden Indizes verwendeten Symbole aufgelistet.  Die Symbole-Abschnitt der VSCT-Datei deklariert die Werte der Bezeichner als Indizes verwendet.  Diese exemplarische Vorgehensweise verwendet den Bitmap-Streifen bereitgestellt, mit der benutzerdefinierte Befehl Elementvorlage zum Projekt hinzugefügt.  
  
 **Platzierungen Abschnitt**.  Nach den Befehlen bildet die Platzierungen-Abschnitt.  Der erste ist, in dem der Code fügt der, dass die erste Gruppe, die erläutert, die vier Spalten Handbuch enthält Befehle aus, um das Untermenü angezeigt, in dem die Befehle:  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 Alle anderen Standorte hinzugefügt haben die `GuidesContextMenuGroup` (enthält die `GuidesSubMenu`) auf anderen Editor-Kontextmenüs.  Wenn der Code deklariert die `GuidesContextMenuGroup`, es wurde ein übergeordnetes Element besitzt, die den Codeeditor-Kontextmenü.  Aus diesem Grund keine Platzierung für das Code-Editor-Kontextmenü angezeigt ist.  
  
 **Symbole im Abschnitt**.  Wie bereits erwähnt, deklariert Symbole im Abschnitt Bezeichner, die an anderer Stelle in der VSCT-Datei, wodurch den VSCT-Code besser lesbar als GUIDs und hexadezimale Ziffern überall verwendet werden.  Die wichtigen Punkte in diesem Abschnitt sind, dass die Paket-GUID mit der Deklaration in der Paketklasse und den Befehlssatz, dass die GUID der Deklaration in der Implementierung Befehlsklasse zustimmen muss übereinstimmen muss.  
  
## <a name="implementing-the-commands"></a>Implementieren die Befehle  
 Die Datei ColumnGuideCommands.cs implementiert die Befehle und die Handler verknüpft.  Wenn Visual Studio wird das Paket geladen und wird initialisiert, ruft das Paket wiederum `Initialize` auf die Befehle Implementierung-Klasse.  Die Initialisierung für die Befehle einfach die Klasse instanziiert, und der Konstruktor der Befehlshandler verknüpft.  
  
 Ersetzen Sie den Inhalt der Datei ColumnGuideCommands.cs durch den folgenden Code (siehe unten):  
  
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
  
 **Korrektur von verweisen**.  Sie sind an diesem Punkt einen Verweis vorhanden.  Drücken Sie die Zeiger nach rechts auf den Knoten "Verweise" im Projektmappen-Explorer.  Wählen Sie die **hinzufügen...**  Befehl.  Die **Verweis hinzufügen** Dialog besitzt ein Suchfeld in der oberen rechten Ecke.  Geben Sie "Editor" (ohne Anführungszeichen) ein.  Wählen Sie die **Microsoft.VisualStudio.Editor** Element (Sie müssen das Kontrollkästchen auf der linken Seite des Elements nicht wählen Sie einfach das Element), und wählen Sie **OK** , den Verweis hinzuzufügen.  
  
 **Initialisierung**.  Wenn die Paketklasse initialisiert wird, ruft er `Initialize` für die Befehle Implementierung-Klasse.  Die `ColumnGuideCommands` Initialisierung die Klasse instanziiert und Klassenmember, werden die Klasseninstanz und der Verweis Paket gespeichert.  
  
 Sehen wir uns einen Befehl Handler Hook USV aus dem Klassenkonstruktor:  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 Sie erstellen eine `OleMenuCommand`.  Visual Studio verwendet das Microsoft Office-System-Befehl.  Die wichtigsten Argumente beim Instanziieren einer OleMenuCommand ist die Funktion, die den Befehl implementiert (`AddColumnGuideExecuted`), die Funktion, die aufgerufen wird, wenn Visual Studio ein Menü mit dem Befehl zeigt (`AddColumnGuideBeforeQueryStatus`), und die Befehls-ID.  Visual Studio Ruft die Abfragefunktion des Status, bevor ein Befehl in einem Menü angezeigt, damit die der Befehl selbst nicht sichtbar oder für eine bestimmte Anzeige des Menüs abgeblendeter kann (z. B. das Deaktivieren **Kopie** , wenn keine Auswahl getroffen wurde), Ändern Sie das Symbol oder sogar ändern Sie den Namen (z. B. von hinzufügen etwas, um etwas zu entfernen), und so weiter.  Die Befehls-ID muss eine Befehls-ID, die Deklaration in der VSCT-Datei übereinstimmen.  Legen Sie die Zeichenfolgen für den Befehl und die Handbüchern Spalte hinzufügen, dass der VSCT-Datei und die ColumnGuideCommands.cs Befehl übereinstimmen muss.  
  
 Die folgende Zeile bietet Unterstützung für, wenn Benutzer den Befehl über das Befehlsfenster (siehe unten) aufrufen:  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **Abfragen des Status**.  Die Status-Abfragefunktionen `AddColumnGuideBeforeQueryStatus` und `RemoveColumnGuideBeforeQueryStatus` überprüfen Sie einige Einstellungen (z. B. die maximale Anzahl von Führungslinien oder max-Spalte) oder wenn eine Spalte-Anleitung zum Entfernen vorhanden ist.  Sie ermöglichen die Befehle, wenn die Bedingungen richtig sind.  Status Abfragefunktionen müssen sehr effizient, da sie jedes Mal ausgeführt, zeigt Visual Studio ein Menü, für jeden Befehl im Menü auf.  
  
 **AddColumnGuideExecuted Funktion**.  Die interessante Teil hinzufügen eine Anleitung ist, den aktuellen Editor-Ansicht und der Einfügemarke Speicherort herauszufinden.  Diese Funktion ruft zuerst `GetApplicableColumn` die überprüft, ob ein Benutzer bereitgestellte Argument in der Befehlshandler Ereignisargumente vorhanden ist, und wenn keine Komponente vorhanden ist, klicken Sie dann die Funktion die Editor-Ansicht überprüft:  
  
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
  
 `GetCurrentEditorColumn` ein kleines abzurufenden verfeinern Sie die Abfrage muss eine <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> Ansicht des Codes.  Wenn Sie über eine Ablaufverfolgung `GetActiveTextView`, `GetActiveView`, und `GetTextViewFromVsTextView`, sehen Sie, wie das geht.  Im folgenden finden Sie den gewünschten Code abstrahiert, beginnend mit der aktuellen Auswahl dann erste Frame mit der Auswahl des Frames DocView als erste eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, abgerufen werden. dann ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> aus der IVsTextView erhalten einen Host anzeigen und zum Schluss die IWpfTextView:  
  
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
  
 Nachdem Sie eine IWpfTextView haben, erhalten Sie die Spalte auf dem sich die Einfügemarke befindet:  
  
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
  
 Mit der aktuellen Spalte, die der Benutzer geklickt hat, ruft manuell in der Code nur auf einstellungs-Manager hinzufügen oder entfernen Sie die Spalte.  Einstellungs-Manager löst das Ereignis aus, auf dem sich alle `ColumnGuideAdornment` Objekte überwachen.  Wenn das Ereignis ausgelöst wird, aktualisieren Sie diese Objekte ihre Ansichten zugeordneten Text mit neue spalteneinstellungen Handbuch.  
  
## <a name="invoking-command-from-the-command-window"></a>Aufrufen der Befehl im Befehlsfenster  
 Die Handbücher spaltenstichprobe kann Benutzer zwei Befehle im Befehlsfenster als eine Form der Erweiterbarkeit aufrufen.  Bei Verwendung der **Ansicht &#124; Weitere Fenster &#124; Befehlsfenster** Befehl können Sie das Befehlsfenster anzeigen.  Sie können das Befehlsfenster interagieren, durch Eingabe von "Bearbeiten", und mit Befehl Vervollständigung von Objektnamen und das Argument 120 bereitstellen, haben Sie die folgenden:  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 Die Teile des Beispiels, die ermöglichen, sind in den Deklarationen der VSCT-Datei, die `ColumnGuideCommands` Klassenkonstruktor, wenn es hooks Befehlshandler und der Befehl Handlerimplementierungen, der Ereignisargumente überprüfen.  
  
 Haben Sie gesehen "`<CommandFlag>CommandWellOnly</CommandFlag>`" in der VSCT-Datei sowie die Platzierungen bearbeiten Sie im Hauptmenü, obwohl es nicht mehr anzeigen der Befehle in der **bearbeiten** Menü UI.  Müssen sie Sie im Hauptmenü bearbeiten erhalten sie Namen wie **Edit.AddColumnGuide**.  Die Befehle zum Gruppieren von Deklaration, die enthält, die vier Befehle der Gruppe "im Menü Bearbeiten direkt platziert:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 Das Schaltflächen-Abschnitt deklariert später die Befehle `CommandWellOnly` , die sie über das Hauptmenü nicht sichtbar bleiben und deklariert mit `AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 Haben Sie gesehen, Verknüpfen von Code im Befehlshandler die `ColumnGuideCommands` Klassenkonstruktor bereitgestellt, eine Beschreibung des Parameters zulässig:  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 Sie gesehen haben die `GetApplicableColumn` Funktion überprüft `OleMenuCmdEventArgs` für einen Wert vor dem Überprüfen der Editor-Ansicht für eine aktuelle Spalte:  
  
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
  
## <a name="trying-your-extension"></a>Versuchen die Erweiterung  
 Sie können jetzt drücken **F5** Spalte Handbücher Erweiterung ausgeführt.  Öffnen Sie eine Textdatei, und verwenden Sie die Editor-Kontextmenü, um die Führungslinien hinzufügen, entfernen Sie sie und ihre Farbe zu ändern.  Müssen Sie in den Text klicken (nicht-Leerzeichen übergeben, das Ende der Zeile) zum Hinzufügen einer Spalte Handbuch oder Editor hinzugefügt die letzte Spalte in der Zeile.  Wenn Sie das Befehlsfenster, und die Befehle mit einem Argument aufrufen, können Sie an einer beliebigen Stelle Handbücher Spalte hinzufügen.  
  
 Wenn Sie verwenden möchten, wiederholen Sie den anderen befehlsplatzierungen, Namen ändern, Ändern von Symbolen und So weiter, und alle Probleme mit Visual Studio den neuesten Code in Menüs angezeigt, können Sie die experimentelle Struktur zurücksetzen, in der Sie debuggen.  Bringen die **Windows-Startmenü** , und geben Sie "Zurücksetzen".  Suchen nach und rufen Sie den Befehl **Zurücksetzen der nächsten Visual Studio experimentellen Instanz**.  Dadurch wird der experimentellen Registrierungsstruktur aller Komponenten der Erweiterung bereinigt.  Dies nicht der Fall Räumen Einstellungen von Komponenten, also alle Handbücher Sie beim Herunterfahren der experimentellen Visual Studio-Struktur mussten werden sein, wenn Code den Store Einstellungen beim nächsten Start liest.  
  
## <a name="finished-code-project"></a>Fertige Codeprojekt  
 Ein Github-Projekt von Visual Studio-Erweiterbarkeit Beispiele bald werden, und das abgeschlossene Projekt vorhanden sein wird.  In diesem Thema, um es zu verweisen, in diesem Fall werden aktualisiert.  Das abgeschlossene Beispielprojekt möglicherweise andere Guids und Farbstreifen verschiedenen Bitmaps für die Befehlssymbole müssen.  
  
 Sie können versuchen, eine Version von der Funktion "Spalte Handbücher" mit diesem Visual Studio Gallery[Erweiterung](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
## <a name="see-also"></a>Siehe auch  
 [Innerhalb des-Editors](../extensibility/inside-the-editor.md)   
 [Erweitern des Editors und des Language-Dienste](../extensibility/extending-the-editor-and-language-services.md)   
 [Sprachdienst und Erweiterungspunkten-Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [Ein Menü hinzugefügt ein Untermenü](../extensibility/adding-a-submenu-to-a-menu.md)   
 [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)