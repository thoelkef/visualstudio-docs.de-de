---
title: Erstellen einer Ansicht Adornment, Befehle und Einstellungen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: f37f2f8243a49f4f85b0f4177f2f33a7a724f08b
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Exemplarische Vorgehensweise: Erstellen einer Ansicht Adornment, Befehle und Einstellungen (Spaltenhilfslinien)
Sie können die Visual Studio-Text-Code-Editor mit Befehlen und Anzeigen von Effekten erweitern.  In diesem Thema erfahren Sie, wie eine beliebte Erweiterungsfunktion Spalten-Einstieg können.  Spalte Handbücher sind visuell helle Linien, die auf den Texteditor-Ansicht helfen Ihnen beim Verwalten von Code, um bestimmte Spaltenbreite gezeichnet.  Speziell formatierten Code kann für Beispiele wichtig sein, Sie sind in Blogbeiträgen-Dokumenten oder Fehlerberichte.  
  
 In dieser exemplarischen Vorgehensweise führen Sie folgende Aktionen ausführen:  
  
-   Erstellen Sie ein VSIX-Projekt  
  
-   Ein Editor-Ansicht Zusatzelement hinzufügen  
  
-   Hinzufügen von Unterstützung für das Speichern und Abrufen von Einstellungen (wobei zum Zeichnen Spalten- und ihre Farbe)  
  
-   Hinzufügen von Befehlen (Hinzufügen/Entfernen von Spalten-, ändern Sie ihre Farbe)  
  
-   Setzen Sie die Befehle im Menü Bearbeiten, und Kontextmenüs für Text-Dokument  
  
-   Hinzufügen von Unterstützung für die Befehle in der Visual Studio-Befehlsfenster aufrufen  
  
 Sie können versuchen, eine Version der Funktion Spalte Handbücher mit diesem Visual Studio Gallery[Erweiterung](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
 **Hinweis**: in dieser exemplarischen Vorgehensweise fügen Sie viel Code in einige Dateien, die visual Studio-Erweiterung Vorlagen generiert werden, aber in dieser exemplarischen Vorgehensweise wird bald finden Sie in eine vollständige Lösung auf Github mit anderen Beispielen für die Erweiterung.  Der fertige Code ist unterschiedlich, darin, dass es real Befehlssymbole statt Generictemplate Symbole besitzt.  
  
## <a name="getting-started"></a>Erste Schritte  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installation von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="setting-up-the-solution"></a>Zum Einrichten der Lösung  
 Zuerst Sie erstellen Sie ein VSIX-Projekt, fügen ein Editor-Ansicht Zusatzelement, und fügen Sie dann einen Befehl (damit ein VSPackage, um den Befehl Besitzer hinzugefügt).  Die grundlegende Architektur lautet wie folgt:  
  
-   Sie haben einen Text anzeigen Erstellung Listener, der erstellt ein `ColumnGuideAdornment` Objekt pro Ansicht.  Dieses Objekt überwacht Ereignisse, die zum Ändern Ansicht oder Einstellungen ändern, aktualisieren oder erneutes Spalte führt nach Bedarf.  
  
-   Es ist ein `GuidesSettingsManager` , lesen und Schreiben in den Speicher der Visual Studio-Einstellungen behandelt.  Der Settings Manager verfügt auch über die Vorgänge zum Aktualisieren der Einstellungen, die der Benutzerbefehle unterstützen (Spalte hinzufügen, entfernt die Spalte, die Farbe ändern).  
  
-   Es ist eine VSIP-Paket, das ist erforderlich, wenn Sie Benutzerbefehle haben allerdings handelt es sich einfach Standardcode, der die Befehle Implementierungsobjekt initialisiert.  
  
-   Es wird ein `ColumnGuideCommands` -Objekt, das implementiert die Benutzerbefehle und bindet die Befehlshandler für Befehle, die in der VSCT-Datei deklariert.  
  
 **VSIX**.  Verwendung **Datei | Neu...** der Befehl zum Erstellen eines Projekts.  Wählen Sie im linken Navigationsbereich der Knoten "Erweiterungen" unter c#, und wählen Sie **VSIX-Projekt** im rechten Bereich.  Geben Sie den Namen ColumnGuides, und wählen Sie **OK** zum Erstellen des Projekts.  
  
 **Anzeigen von Adornment**.  Drücken Sie die Zeiger auf den Projektknoten im Projektmappen-Explorer.  Wählen Sie die **hinzufügen | Neues Element...** Befehl zum Hinzufügen eines neuen Ansicht Randsteuerelement-Elements.  Wählen Sie **Erweiterbarkeit | Editor** im linken Navigationsbereich, und wählen Sie **Editor Viewport Adornment** im rechten Bereich.  Geben Sie den Namen ColumnGuideAdornment als Name des Elements, und wählen Sie **hinzufügen** hinzufügen.  
  
 Sie sehen, dass diese Elementvorlage zwei Dateien dem Projekt (sowie Verweise und usw.) hinzugefügt: ColumnGuideAdornment.cs und ColumnGuideAdornmentTextViewCreationListener.cs.  Die Vorlagen Rechteck nur ein Lila für die Sicht.  Im folgenden Sie ein paar Zeilen in der Ansicht Erstellung Listener ändern und Ersetzen Sie den Inhalt des ColumnGuideAdornment.cs.  
  
 **Befehle**.  Drücken Sie die Zeiger auf den Projektknoten im Projektmappen-Explorer.  Wählen Sie die **hinzufügen | Neues Element...** Befehl zum Hinzufügen eines neuen Ansicht Randsteuerelement-Elements.  Wählen Sie **Erweiterbarkeit | VSPackage** im linken Navigationsbereich, und wählen Sie **Befehl benutzerdefinierte** im rechten Bereich.  Geben Sie den Namen ColumnGuideCommands als Name des Elements, und wählen Sie **hinzufügen** hinzufügen.  ColumnGuideCommands.cs, ColumnGuideCommandsPackage.cs und ColumnGuideCommandsPackage.vsct sowie mehrere Verweise hinzugefügt der Befehle und das Paket hinzufügen.  Im folgenden wird der Inhalt der ersten und letzten Dateien definieren und implementieren die Befehle ersetzt.  
  
## <a name="setting-up-the-text-view-creation-listener"></a>Der Text anzeigen Erstellung Listener einrichten  
 Öffnen Sie ColumnGuideAdornmentTextViewCreationListener.cs im Editor.  Dieser Code wird ein Handler implementiert, wenn Visual Studio Textansichten erstellt.  Attribute, mit denen gesteuert wird, wenn der Ereignishandler aufgerufen wird, je nach den Eigenschaften der Ansicht sind vorhanden.  
  
 Der Code muss auch eine Randsteuerelement-Ebene deklariert werden.  Wenn der Editor Sichten aktualisiert, ruft die Adornment Ebenen für die Ansicht und, ruft die Randsteuerelement-Elemente.  Sie können deklarieren, die Reihenfolge der Ebene relativ zu anderen Attribute.  Ersetzen Sie die folgende Zeile:  
  
```c#  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 mit diesen zwei Zeilen:  
  
```c#  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 Die Zeile, die Sie ersetzt wird in eine Gruppe von Attributen, die eine Adornmentebene deklarieren.   Die erste Zeile geändert Sie nur ändern, wo die Spalte Hilfslinien angezeigt werden.  Zeichnen von Linien "vor" der Text in der Ansicht bedeutet, dass sie hinter oder unter dem Text angezeigt werden.  Die zweite Zeile deklariert, dass die Spalte Handbuch Zusatzelemente gelten für Text-Elemente, die Ihre Konzept eines Dokuments zu passen, aber Sie das Zusatzelement z. B. nur die Arbeit für den Text bearbeitet werden deklarieren.  Weitere Informationen stehen im [Sprachdienst und Erweiterungspunkte-Editor](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>Implementieren des Settings Managers  
 Ersetzen Sie den Inhalt der GuidesSettingsManager.cs durch den folgenden Code (siehe unten):  
  
```c#  
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
  
 Dieser Code einfach erstellt und analysiert die Settings-Format: "RGB (\<Int >,\<Int >,\<Int >) \<Int >, \<Int >,...".  Die Ganzzahlen am Ende sind die&1;-basierte Spalten Spalten-werden soll.  Die Spalte Handbücher Erweiterung erfasst alle Einstellungen in eine einzelne Einstellung Wert ein.  
  
 Es gibt einige Teile des Codes zu markieren.  Die folgende Codezeile Ruft den Visual Studio-Wrapper für die Speicherung von Einstellungen.  Zum größten Teil dieses abstrahiert, über die Windows-Registrierung, aber diese API ist unabhängig von den Speichermechanismus.  
  
```c#  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Der Visual Studio-Einstellungen-Speicher verwendet eine Kategorie-ID und einer Einstellung-ID zur eindeutigen Identifizierung der alle Einstellungen:  
  
```c#  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 Sie müssen keinen verwenden `“Text Editor”` als Kategorie Namen, und Sie können auswählen, beliebig.  
  
 Die ersten einige Funktionen sind Einstiegspunkte zu ändern.  Sie prüfen, ob allgemeine Einschränkungen wie die maximale Anzahl von Hilfslinien zulässig.  Anschließend sie rufen `WriteSettings` die verfasst einer Settings-Zeichenfolge und legt die Eigenschaft `GuideLinesConfiguration`.  Durch Festlegen dieser Eigenschaft der Einstellungswert speichert, in der Visual Studio-Einstellungen speichern und löst die `SettingsChanged` Ereignis alle aktualisieren die `ColumnGuideAdornment` Objekte, die jeweils eine Textansicht zugeordnet.  
  
 Es gibt eine Reihe von Funktionen für Eingabe, wie `CanAddGuideline`, mit denen die Befehle zu implementieren, die Einstellungen zu ändern.  Wenn Visual Studio Menüs angezeigt wird, wird abgefragt, usw. Befehl Implementierungen, um festzustellen, ob der Befehl derzeit aktiviert ist, was ist der Name.  Im folgenden sehen Sie, wie diese Einstiegspunkte für den Befehl Implementierungen verknüpft.  Finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md) für Weitere Informationen zu Befehlen.  
  
## <a name="implementing-the-columnguideadornment-class"></a>Implementierung der ColumnGuideAdornment-Klasse  
 Die `ColumnGuideAdornment` für jede Textansicht Zusatzelemente denen Klasse instanziiert wird.  Diese Klasse überwacht Ereignisse im Zusammenhang mit der Ansicht ändern oder Einstellungen ändern, aktualisieren oder erneutes Spalte führt nach Bedarf.  
  
 Ersetzen Sie den Inhalt der ColumnGuideAdornment.cs durch den folgenden Code (siehe unten):  
  
```c#  
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
  
 Instanzen dieser Klasse enthalten, auf die zugeordnete <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>und eine Liste der `Line` Objekte, die in der Ansicht gezeichnet.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>  
  
 Der Konstruktor (aufgerufen `ColumnGuideAdornmentTextViewCreationListener` Wenn Visual Studio werden neue Ansichten erstellt) erstellt das Handbuch Spalte `Line` Objekte.  Der Konstruktor fügt auch Handler für das `SettingsChanged` Ereignis (definiert `GuidesSettingsManager`) und die Ereignisse anzeigen `LayoutChanged` und `Closed`.  
  
 Die `LayoutChanged` Ereignis ausgelöst wird, aufgrund der verschiedenen Arten von Änderungen in der Ansicht, wenn Visual Studio die Ansicht erstellt.  Die `OnViewLayoutChanged` Ereignishandler ruft `AddGuidelinesToAdornmentLayer` ausführen.  Der Code in `OnViewLayoutChanged` bestimmt, ob die Zeile Positionen basierend auf Änderungen wie z. B. Schriftgrad ändert sich, Gitternetzlinien anzeigen, horizontalen Bildlauf und So weiter aktualisiert werden muss.  Der Code in `UpdatePositions` bewirkt, dass Hilfslinien zwischen Zeichen oder unmittelbar nach der Spalte der Text in der angegebenen Zeichenoffset in die Zeile des Texts gezeichnet.  
  
 Bei jedem Ändern der `SettingsChanged` Funktion erstellt alle nur die `Line` Objekte mit beliebigen die neuen Einstellungen werden.  Nach dem Festlegen der Zeile Positionen, entfernt der Code alle vorherigen `Line` -Objekte aus der `ColumnGuideAdornment` Adornmentebene und fügt die neuen Dateien.  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>Definieren die Befehle, Menüs und Platzierungen im Menü  
 Möglich viel zu deklarieren, Befehle und Menüs, Gruppen von Befehlen oder Menüs auf verschiedenen anderen Menüs platzieren und Befehlshandler einbinden.  In dieser exemplarischen Vorgehensweise werden hervorgehoben, wie Befehle in dieser Erweiterung, aber tiefer Informationen funktionieren, finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).  
  
### <a name="introduction-to-the-code"></a>Einführung in den Code  
 Die Erweiterung Spalten-zeigt deklarieren eine Gruppe von Befehlen, die zusammen gehören (Spalte hinzufügen, entfernen Sie die Spalte, Linienfarbe ändern), und speichern diese Gruppe in einem Menü Sub des Kontextmenüs des Editors.  Die Erweiterung Spalten-fügt auch die Befehle an den Haupt- **bearbeiten** Menü jedoch verhindert, nicht sichtbar ist, als ein allgemeines Muster, die weiter unten erläutert.  
  
 Es gibt drei Teile der Implementierung Befehle: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct und ColumnGuideCommands.cs.  Von den Vorlagen generierte Code stellt einen Befehl in der **Tools** wie bei der Implementierung ein Dialogfeld angezeigt.  Sie untersuchen, die Implementierung in der VSCT und ColumnGuideCommands.cs-Dateien, da es ziemlich einfach ist.  Sie ersetzen Sie den Code in diesen Dateien.  
  
 Der Paketcode ist Textbausteine-Deklarationen, die für Visual Studio festzustellen, ob die Erweiterung Befehle und platzieren Sie die Befehle bietet erforderlich sind.  Wenn das Paket initialisiert wird, instanziiert die Implementierungsklasse Befehle.  Finden Sie die Befehle, die über weitere Informationen über Pakete, die im Zusammenhang mit den Befehlen zu verknüpfen.  
  
### <a name="a-common-commands-pattern"></a>Ein häufiges Muster für Befehle  
 Die Befehle in der Spalte Handbücher-Erweiterung sind ein Beispiel für ein weit verbreitetes Muster in Visual Studio.  Setzen Sie verwandte Befehle in einer Gruppe, und stellen diese Gruppe auf ein Hauptmenü häufig mit "`<CommandFlag>CommandWellOnly</CommandFlag>`" festgelegt, um den Befehl unsichtbar zu machen.  Befehle in den Hauptmenüs platzieren (z. B. **bearbeiten**) auf diese Weise erhalten sie eine gute Namen (z. B. **Edit.AddColumnGuide**) eignen sich für die Suche nach Befehlen beim Neuzuweisen von Tastenkombinationen in **Optionen** und zum Abschluss abrufen, beim Aufrufen der Befehle aus der **Befehlsfenster**.  
  
 Klicken Sie anschließend die Gruppe von Befehlen zu Kontextmenüs hinzufügen oder sub-Menüs, wo Benutzer mit den Befehlen zu erwarten.  Visual Studio behandelt `CommandWellOnly` als ein unsichtbarkeits-Flag für nur Hauptmenüs.  Wenn Sie die gleiche Gruppe von Befehlen in einem Kontextmenü oder Sub-Menü platzieren, sind die Befehle angezeigt.  
  
 Als Teil eines allgemeinen Musters erstellt die Erweiterung Spalten-eine zweite Gruppe, die eine einzelne Untermenü enthält.  Das Untermenü enthält wiederum die erste Gruppe mit vier Spalten Handbuch Befehlen.  Die zweite Gruppe, die das Untermenü enthält, ist die wieder verwendbare Ressource, die Sie in verschiedenen Kontextmenüs, platzieren, die auf die Kontextmenüs Untermenü versetzt.  
  
### <a name="the-vsct-file"></a>Die VSCT-Datei  
 Die VSCT-Datei werden die Befehle und, zusammen mit Symbolen und wo sie deklariert.  Ersetzen Sie den Inhalt der .vsct-Datei durch den folgenden Code (siehe unten):  
  
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
  
 **GUIDS**.  Für Visual Studio der Befehlshandler suchen und diese aufzurufen müssen Sie sicherstellen, dass das Paket, das GUID in der ColumnGuideCommandsPackage.cs-Datei (aus der Projektelementvorlage generiert) deklariert, das Paket übereinstimmt, das GUID in der VSCT-Datei (von oben kopiert) deklariert.  Wenn Sie diesen Beispielcode erneut verwenden, sollten Sie sicherstellen, dass Sie eine andere GUID verfügen, sodass Sie nicht mit anderen Personen Konflikte verursachen, die diesen Code kopiert haben, können.  
  
 Suchen Sie folgende Zeile in ColumnGuideCommandsPackage.cs, und kopieren Sie die GUID von einschließlich der Anführungszeichen:  
  
```c#  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 Fügen Sie die GUID in der VSCT-Datei, sodass Sie die folgende Zeile Ihre `Symbols` Deklarationen:  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 Legen Sie die GUIDs für den Befehl, und die Bitmap-Image-Datei sollte zu den Erweiterungen eindeutig sein:  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 Sie müssen allerdings nicht zu ändern, den Befehlssatz bitmap-Bild-GUIDs in dieser exemplarischen Vorgehensweise, um den Code zu erhalten zu können.  Den Befehlssatz GUID muss die Deklaration in der Datei ColumnGuideCommands.cs überein, aber ersetzen Sie den Inhalt der Datei zu. Daher werden die GUIDs übereinstimmen.  
  
 Andere GUIDs in der VSCT-Datei identifizieren bereits vorhandenen Menüs, die Spalte Handbuch Befehle hinzugefügt werden, so dass sie nie ändern.  
  
 **Abschnitte der Datei**.  Die VSCT besteht aus drei äußeren Abschnitten: Befehle, Standorte und Symbole.  Im Abschnitt Befehle definiert Befehlsgruppen, Menüs, Schaltflächen oder Menüelemente und Bitmaps für Symbole.  Abschnitt Platzierungen deklariert, wo Gruppen auf Menüs oder zusätzliche Standorte auf bereits vorhandenen Menüs.  Abschnitt Symbole werden an anderer Stelle in der VSCT-Datei, wodurch den VSCT-Code besser lesbar als GUIDs und Hexadezimalzahlen überall verwendeten Bezeichner deklariert.  
  
 **Befehle im Abschnitt, Gruppen oder Definitionen**.  Im Abschnitt Befehle definiert zuerst Befehlsgruppen.  Gruppen von Befehlen sind Befehle, die in Menüs mit geringfügigen grauen Trennlinien Gruppen angezeigt.  Eine Gruppe kann auch eine gesamte Untermenü, wie in diesem Beispiel ausfüllen und die graue, trennen die Zeilen in diesem Fall nicht angezeigt.  VSCT-Dateien deklariert zwei Gruppen, die `GuidesMenuItemsGroup` , übergeordnet ist die `IDM_VS_MENU_EDIT` (im Hauptfenster **bearbeiten** Menü) und die `GuidesContextMenuGroup` , übergeordnet ist der `IDM_VS_CTXT_CODEWIN` (der Code-Editor-Kontextmenü).  
  
 Die zweite Gruppendeklaration wurde ein `0x0600` Priorität:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 Die Idee ist die Spalte einzufügenden Untermenü am Ende führt eines Kontextmenüs, die wir Sub Menügruppe hinzu.  Allerdings sollten Sie nicht davon ausgehen Sie am besten kennen, und erzwingen das Untermenü immer das letzte ist mit einer Priorität von `0xFFFF`.  Haben Sie diese Nummer, um festzustellen, wo das Sub-Menü auf die Kontextmenüs liegt an experimentieren.  In diesem Fall `0x0600` hoch genug ist, am Ende des Menüs abzulegen, als wir sehen, lässt jedoch auch Raum für jemand anderen entwerfen Sie ihre Erweiterung niedriger sein als die Spalte Handbücher Erweiterung ist dies wünschenswert ist.  
  
 **Befehle im Menü Definition im Abschnitt**.  Als Nächstes im Abschnitt-Befehl definiert das Untermenü `GuidesSubMenu`, übergeordnetes Element, um die `GuidesContextMenuGroup`.  Die `GuidesContextMenuGroup` ist die Gruppe, die wir zu den relevanten Kontextmenüs hinzufügen.  Im Abschnitt Platzierungen platziert der Code die Gruppe mit vier Spalten Handbuch Befehlen in diesem Menü Sub.  
  
 **Abschnitt Befehle, Schaltflächen Definitionen**.  Im Abschnitt Befehle definiert dann die Menüelemente oder Schaltflächen, die vier Spalten werden, führt Befehle.  `CommandWellOnly`, weiter oben erläuterten, bedeutet dies, dass die Befehle ausgeblendet, wenn auf ein Hauptmenü platziert.  Zwei des Menüelements Schaltfläche Deklarationen (Führungslinie hinzufügen und Entfernen von Handbuch) auch ein `AllowParams` Kennzeichen:  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 Mit diesem Flag kann zusammen mit Hauptmenü Platzierungen, den Befehl, um Argumente zu empfangen, wenn Visual Studio den Befehlshandler aufruft.  Wenn der Benutzer den Befehl im Befehlsfenster aufruft, ruft das Argument an den Befehlshandler im Argumente übergeben.  
  
 **Befehl Abschnitte, Bitmaps Definitionen**.  Schließlich deklariert Abschnitt Befehlen die Bitmaps oder Symbole, die für die Befehle verwendet.  Dies ist eine einfache Deklaration, die die Projektressource identifiziert, und eins Indizes verwendeten Symbole aufgelistet.  Im Abschnitt "Symbole" der .vsct-Datei deklariert die Werte als Indizes verwendeten Bezeichner.  Diese exemplarische Vorgehensweise verwendet den Bitmap-Streifen bereitgestellt, mit der benutzerdefinierten Befehl Elementvorlage zum Projekt hinzugefügt.  
  
 **Standorte Abschnitt**.  Nach den Befehlen bildet die Platzierungen-Abschnitt.  Die erste ist die erste Gruppe erläutert, die im Handbuch für die vier Spalten enthält Befehle aus, um das Untermenü angezeigt, in dem die Befehle, in denen der Code hinzugefügt:  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 Alle anderen Standorte hinzufügen die `GuidesContextMenuGroup` (enthält die `GuidesSubMenu`) auf anderen Editor-Kontextmenüs.  Wenn der Code deklariert die `GuidesContextMenuGroup`, sie wurde dem Kontextmenü des Code-Editor untergeordnet.  Eine Position für den Codeeditor-Kontextmenü nicht angezeigt wird.  
  
 **Symbole im Abschnitt**.  Wie bereits erwähnt, deklariert Abschnitt Symbole Bezeichner, die an anderer Stelle in der VSCT-Datei, wodurch den VSCT-Code besser lesbar als GUIDs und Hexadezimalzahlen überall verwendet werden.  Die wichtigen Informationen in diesem Abschnitt sind die Paket-GUID mit der Deklaration in der Klasse und den Befehlssatz, dass die GUID mit der Deklaration in der Klasse des Befehls Implementierung zustimmen muss übereinstimmen muss.  
  
## <a name="implementing-the-commands"></a>Implementieren die Befehle  
 Die ColumnGuideCommands.cs-Datei implementiert die Befehle und die Ereignishandler verknüpft.  Wenn Visual Studio wird das Paket geladen und initialisiert, das Paket im Gegenzug `Initialize` auf die Implementierungsklasse Befehle.  Die Initialisierung Befehle einfach die Klasse instanziiert, und der Konstruktor die Befehlshandler verknüpft.  
  
 Ersetzen Sie den Inhalt der Datei ColumnGuideCommands.cs durch den folgenden Code (siehe unten):  
  
```c#  
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
  
 **Korrektur von verweisen**.  Einen Verweis fehlt an dieser Stelle.  Drücken Sie die Zeiger auf den Knoten "Verweise" im Projektmappen-Explorer.  Wählen Sie die **hinzufügen...** Befehl.  Die **Verweis hinzufügen** Dialog besitzt ein Suchfeld in der oberen rechten Ecke.  Geben Sie "Editor" (ohne Anführungszeichen) ein.  Wählen Sie die **Microsoft.VisualStudio.Editor** Element (muss das Kontrollkästchen links neben dem Element, nicht nur wählen das Element), und wählen Sie **OK** , den Verweis hinzuzufügen.  
  
 **Initialisierung**.  Wenn die Klasse initialisiert wird, ruft es `Initialize` auf die Implementierungsklasse Befehle.  Das `ColumnGuideCommands` Initialisierung instanziiert die Klasse und speichert die Klasseninstanz und der Paketverweis in der Klassenmember.  
  
 Betrachten eines Befehls Handler Hook USV Klassenkonstruktor:  
  
```c#  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 Erstellen Sie eine `OleMenuCommand`.  Visual Studio verwendet das Microsoft Office-System-Befehl.  Die wichtigsten Argumente beim Instanziieren einer OleMenuCommand ist die Funktion, die mit dem Befehl implementiert (`AddColumnGuideExecuted`), die aufzurufende Funktion, wenn Visual Studio ein Menü mit dem Befehl zeigt (`AddColumnGuideBeforeQueryStatus`), und die Befehls-ID.  Visual Studio Ruft die Abfrage Status-Funktion, bevor Sie einen Befehl in einem Menü angezeigt wird, damit die mit dem Befehl selbst nicht sichtbar oder für eine bestimmte Anzeige des Menüs abgeblendeten kann (z. B. das Deaktivieren **Kopie** , wenn keine Auswahl vorhanden ist), dessen Symbol ändern oder sogar ändern Sie den Namen (z. B. von hinzufügen etwas entfernen etwas) usw..  Die Befehls-ID muss eine Befehls-ID, die in der VSCT-Datei deklariert übereinstimmen.  Legen Sie die Zeichenfolgen für den Befehl und die Spalte Handbücher fügen Sie der VSCT-Datei und die ColumnGuideCommands.cs Befehl übereinstimmen muss.  
  
 Die folgende Zeile bietet Unterstützung für Benutzer den Befehl über das Befehlsfenster (siehe unten) aufgerufen werden:  
  
```c#  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **Status Abfragen**.  Der Status Abfragefunktionen `AddColumnGuideBeforeQueryStatus` und `RemoveColumnGuideBeforeQueryStatus` überprüfen Sie einige Einstellungen (z. B. die maximale Anzahl von Führungslinien oder max-Spalte) oder wenn es Spalte Hinweise zu entfernen.  Sie ermöglichen die Befehle, wenn die Bedingung richtig sind.  Status Abfragefunktionen sehr effizient, da sie jedes Mal, zeigt Visual Studio ein Menü für jeden Befehl im Menü ausgeführt werden müssen.  
  
 **AddColumnGuideExecuted-Funktion**.  Der interessante Teil beim Hinzufügen einer Anleitung ist, die aktuelle Ansicht und der Einfügemarke Editorposition herauszufinden.  Diese Funktion ruft zunächst `GetApplicableColumn` die überprüft, ob eine vom Benutzer angegebenen Argument in der Befehlshandler Ereignisargumente vorhanden ist, und wenn keine Komponente vorhanden ist, klicken Sie dann die Funktion die Editor Ansicht überprüft:  
  
```c#  
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
  
 `GetCurrentEditorColumn`hat etwas abzurufenden rekonstruieren ein <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>die Codeansicht.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>  Wenn Sie über verfolgen `GetActiveTextView`, `GetActiveView`, und `GetTextViewFromVsTextView`, sehen Sie, wie das geht.  Im folgenden ist der entsprechende Code abstrahiert, beginnend mit der aktuellen Auswahl dann erste Frame für die Auswahl des Frames DocView als erste eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, anschließend eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>aus der IVsTextView anschließend abgerufen, ein View-Host und schließlich die IWpfTextView:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
```c#  
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
  
 Nachdem Sie eine IWpfTextView haben, erhalten Sie die Spalte, wo sich die Einfügemarke befindet:  
  
```c#  
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
  
 Mit der aktuellen Spalte, die der Benutzer geklickt hat, ruft in der Code nur auf der Settings Manager hinzufügen oder entfernen Sie die Spalte.  Der Settings Manager löst das Ereignis aus, um alle `ColumnGuideAdornment` Objekte zu überwachen.  Wenn das Ereignis ausgelöst wird, aktualisieren diese Objekte ihre Ansichten zugeordneten Text mit neuen Spalte Handbuch Einstellungen.  
  
## <a name="invoking-command-from-the-command-window"></a>Aufrufen der Befehl im Befehlsfenster  
 Die Spalte Handbücher Beispiel kann Benutzer zwei Befehle im Befehlsfenster als eine Form der Erweiterung aufgerufen.  Bei Verwendung der **anzeigen | Andere Fenster | Befehlsfenster** Befehl sehen Sie das Befehlsfenster.  Mit dem Befehlsfenster können durch Eingabe von "Bearbeiten", und mit Befehl Vervollständigung und das Argument 120 bereitstellen, haben Sie die folgenden:  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 Die Teile des Beispiels, die ermöglichen, sind in den Deklarationen der VSCT-Datei, die `ColumnGuideCommands` Klassenkonstruktor, wenn er nimmt Befehlshandler Implementierung und der Befehl Ereignishandler, die Ereignisargumente überprüfen.  
  
 Sie haben gesehen, "`<CommandFlag>CommandWellOnly</CommandFlag>`" in der VSCT-Datei sowie die Platzierung im Hauptmenü bearbeiten, obwohl es nicht mehr anzeigen die Befehle in der **bearbeiten** Menü Benutzeroberfläche.  Wenn diese Menü Bearbeiten erhalten sie Namen wie **Edit.AddColumnGuide**.  Die Befehle gruppieren die Deklaration, die enthält vier Befehle die Gruppe im Menü Bearbeiten direkt platziert:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 Der Abschnitt die Befehle später deklariert `CommandWellOnly` um jeden unsichtbar im Hauptmenü und deklariert mit `AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 Sie haben gesehen, den Befehlshandler Einbinden von Code in die `ColumnGuideCommands` Klassenkonstruktor eine Beschreibung des Parameters zulässige bereitgestellt:  
  
```c#  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 Sie haben gesehen, die `GetApplicableColumn` Funktion überprüft `OleMenuCmdEventArgs` für einen Wert vor der Prüfung der Editor-Ansicht für eine aktuelle Spalte:  
  
```c#  
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
 Sie können jetzt drücken **F5** Spalten-Erweiterung ausführen.  Öffnen Sie eine Textdatei, und verwenden Sie die Editor Kontextmenü Führungslinien hinzufügen, entfernen und ändern ihre Farbe.  Müssen Sie im Text-Format (kein Leerzeichen übergeben, das Ende der Zeile) zum Hinzufügen einer Spalte Handbuch oder im Editor hinzugefügt die letzte Spalte in der Zeile.  Wenn Sie das Befehlsfenster, und die Befehle mit einem Argument aufrufen, können Sie überall Handbücher Spalte hinzufügen.  
  
 Wenn Probleme mit Visual Studio, die den aktuellen Code in den Menüs angezeigt, und wiederholen Sie den Befehl Platzierungen, Namen ändern, ändern, Symbole usw. werden sollen, können Sie die experimentelle Struktur zurücksetzen, in der Sie debuggen.  Rufen Sie die **Windows-Startmenü** , und geben Sie "reset".  Suchen nach und rufen Sie den Befehl **Zurücksetzen der nächsten Visual Studio experimentelle Instanz**.  Die experimentelle Registrierungsstruktur aller Komponenten der Erweiterung bereinigt.  Nicht Räumen Einstellungen von Komponenten, also alle Hilfslinien Sie beim Herunterfahren experimentellen Visual Studio-Struktur mussten werden sein, wenn der Code den einstellungsspeicher beim nächsten Start liest.  
  
## <a name="finished-code-project"></a>Fertige Codeprojekt  
 Gibt es in Kürze ein Github-Projekt von Visual Studio-Erweiterbarkeit Beispiele, und das fertige Projekt vorhanden ist.  In diesem Thema zeigen es in diesem Fall werden aktualisiert.  Das abgeschlossene Beispielprojekt möglicherweise andere Guids und muss einen Streifen mit verschiedenen Bitmaps für den Befehlssymbole.  
  
 Sie können versuchen, eine Version der Funktion Spalte Handbücher mit diesem Visual Studio Gallery[Erweiterung](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
## <a name="see-also"></a>Siehe auch  
 [Im Editor](../extensibility/inside-the-editor.md)   
 [Erweitern der-Editor und Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)   
 [Language Service und Erweiterungspunkte-Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)   
 [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)   
 [Erstellen eine Erweiterung mit einer Elementvorlage-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)
