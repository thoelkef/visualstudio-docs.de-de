---
title: Unterstützung für die Monitorspezifische dpi-Erkennung für Visual Studio-Extender
titleSuffix: ''
description: Erfahren Sie, bis die neue Extender-Unterstützung für pro-Monitor-Unterstützung in Visual Studio-2019 verfügbar.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 44938c5753491521702867398a514f770cf831fb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099389"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Unterstützung für die Monitorspezifische dpi-Erkennung für Visual Studio-Extender
Versionen vor Visual Studio-2019 mussten die DPI-Wert-Awareness-Kontext auf System fähig ist, anstatt monitorspezifische dpi-DPI-bewusst (PMA) festgelegt. System Awareness auf führte zu einer beeinträchtigten Visualisierung (z. B. unscharf Schriftarten oder Symbolsatz) auftreten, wenn musste, dass Visual Studio über Monitore mit verschiedenen Skalierungsfaktoren oder Remote in Computern mit verschiedenen Anzeigekonfigurationen z. B. (unterschiedliche Rendern Windows-Skalierung).

Visual Studio-2019 Kontext Awareness DPI-Wert wird als PMA, festgelegt, wenn die Umgebung unterstützt, da Visual Studio entsprechend der Konfiguration der Anzeige gerendert, wo sie gehostet wird, anstelle einer einzigen System definierten Konfiguration. Letztlich Übersetzung in eine immer schärfer Benutzeroberfläche für Oberflächen, die PMA Modus unterstützen.

Finden Sie in der [hohe DPI-Wert Desktop-Anwendungsentwicklung unter Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) Dokumentation für Weitere Informationen über die Bedingungen und das allgemeine Szenario in diesem Dokument behandelt.

## <a name="quickstart"></a>Schnellstart
- Stellen Sie sicher, Visual Studio im PMA-Modus ausgeführt wird (siehe **PMA aktivieren**)

- Überprüfen Sie Ihre Erweiterung funktioniert ordnungsgemäß, auf eine Reihe von Szenarios (finden Sie unter **Testen Ihre Erweiterungen für PMA Probleme**)

- Wenn Sie Probleme feststellen, können Sie die in diesem Dokument beschriebenen Strategien/Empfehlungen zum Diagnostizieren und beheben diese Probleme. Sie müssen auch das Hinzufügen der neuen [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet-Paket zum Projekt, um den erforderlichen Zugriff auf APIs.

## <a name="enabling-pma"></a>Aktivieren der PMA
Um PMA in Visual Studio zu aktivieren, müssen die folgenden Anforderungen erfüllt sein:
1) Windows 10 April 2018 Update (Version RS4 v1803) oder höher
2) .NET Framework 4.8 RTM oder höher
3) Visual Studio-2019 mit der ["Optimieren des Renderings für Bildschirme mit verschiedenen Pixel dichten"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) Option aktiviert ist

Wenn diese Anforderungen erfüllt sind, wird Visual Studio automatisch über den Prozess PMA-Modus aktiviert.

> [!NOTE]
> Windows Forms-Inhalt in Visual Studio (z. B. Eigenschaften-Browser) unterstützt die PMA nur, wenn Sie Visual Studio 2019 Update 1 verfügen.

## <a name="testing-your-extensions-for-pma-issues"></a>Testen Ihre Erweiterungen für PMA-Probleme

Visual Studio unterstützt offiziell die WPF, Windows Forms, Win32- und HTML/JS-UI-Frameworks. Wenn Visual Studio in den PMA Modus versetzt wird, verhält sich anders jedes UI-Stapel. Aus diesem Grund wird unabhängig vom Benutzeroberflächen-Frameworks empfohlen, dass ein Testdurchlauf ausgeführt wird, um sicherzustellen, dass alle UI mit PMA Modus kompatibel ist.

Es wird empfohlen, dass Sie die folgenden gängigen Szenarien überprüfen:

1. Den Skalierungsfaktor einer einzelnen Monitor Umgebung ändern, während die Anwendung ausgeführt wird. *
    - Dieses Szenario hilft dabei, testen, ob die Benutzeroberfläche reagiert auf die dynamische Windows-DPI-Änderung

2. Verankern lösen und einen Laptop, bei dem ein angeschlossenen Monitor mit dem primären Replikat festgelegt ist und des angeschlossenen Monitors einen anderen Skalierungsfaktor als der Laptop während der Anwendung ausgeführt wird.
    - Dieses Szenario hilft dabei, testen, ob die Benutzeroberfläche auf dem Bildschirm reagiert, DPI-Änderung sowie das Behandeln von zeigt dynamisch hinzugefügt oder entfernt wird

3. Müssen mehrere Monitore mit verschiedenen Skalierungsfaktor, und verschieben Sie die Anwendung zwischen ihnen.
    - Dieses Szenario hilft dabei, testen, ob die Benutzeroberfläche reagiert auf die Anzeige DPI-Änderung
    
4. Remoting auf einem Computer, wenn die lokale und remote-Computer andere Skalierungsfaktoren für den primären Monitor besitzen.
    - Dieses Szenario hilft dabei, testen, ob die Benutzeroberfläche reagiert auf die dynamische Windows-DPI-Änderung

Wird ein vorläufiger Test gibt an, ob die Benutzeroberfläche manchmal Probleme auftreten, gibt an, ob der Code nutzt die *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*, *Microsoft.VisualStudio.PlatformUI.DpiHelper*, oder *VsUI::CDpiHelper* Klassen. Diese alten DpiHelper Klassen unterstützen nur die System-DPI-Unterstützung und wird nicht immer ordnungsgemäß, wenn der Prozess PMA ist.

Typische Verwendung der folgenden DpiHelpers sieht so aus wie:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

Im vorherigen Beispiel wird ein Rechteck, das die logischen Begrenzungen eines Fensters darstellt in Geräteeinheiten konvertiert, damit es an die systemeigene Methode MonitorFromPoint übergeben werden kann, die Gerätekoordinaten erwartet wird, um eine genaue Überwachung Zeiger zurückgegeben.

### <a name="classes-of-issues"></a>Klassen von Problemen
Wenn PMA Modus für Visual Studio aktiviert ist, konnte in die Benutzeroberfläche in mehrere gängige Möglichkeiten der Probleme repliziert werden. Die meisten, wenn nicht alle möglich diese Probleme in einem der unterstützten Visual Studio Benutzeroberflächen-Frameworks. Darüber hinaus dieser Probleme können auch auftreten, wenn ein Element der Benutzeroberfläche im gemischten Modus-DPI-Skalierung Szenarien gehostet wird (finden Sie in der Windows [Dokumentation](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) Weitere). 

#### <a name="win32-window-creation"></a>Erstellen von Win32-Fenster
Wenn Sie Windows mit CreateWindow() oder CreateWindowEx() erstellen zu können, ist ein gängiges Muster zum Erstellen des Fensters an Koordinaten (0,0) (/ linken oberen Ecke der primären Anzeige), klicken Sie dann auf die letzte Position verschieben. Das Fenster zum Auslösen der DPI-Wert kann dazu führen, dass dies jedoch geändert, Nachricht oder des Ereignisses, die auch andere UI-Nachrichten oder Ereignisse erneut auslösen, und schließlich Rendering zu unerwünschtem Verhalten führen kann.

#### <a name="wpf-element-placement"></a>Platzierung der WPF-element
Beim Verschieben von WPF-Elemente, die mit der alten Microsoft.VisualStudio.Utilities.Dpi.DpiHelper möglicherweise Koordinaten der oberen linken nicht ordnungsgemäß berechnet werden, wenn Elemente in einem nicht primären DPI sind.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialisierung von UI-Element-Größe und Position
Wenn UI-Größe oder Position (Wenn als Geräteeinheiten gespeichert), auf einem anderen DPI-Kontext wiederhergestellt wird als was sie am gespeichert wurde, wird er positioniert und Größe nicht ordnungsgemäß. Dies geschieht, weil Geräteeinheiten eine inhärente DPI-Beziehung aufweisen.

#### <a name="incorrect-scaling"></a>Falsche Skalierung
UI-Elemente, die auf den primären DPI-Wert erstellt werden ordnungsgemäß skaliert werden, jedoch beim Verschieben auf einen Monitor mit einer anderen DPI-Wert, sie nicht skalieren und daher ihren Inhalt im Endeffekt zu groß oder klein ist.

#### <a name="incorrect-bounding"></a>Falsche umgebenden
Auf ähnliche Weise für die Skalierung Problem berechnet Elemente der Benutzeroberfläche ihre Grenzen ordnungsgemäß auf ihrem primären DPI-Kontext, jedoch, wenn in einem nicht primären DPI verschoben, die neuen Grenzen ordnungsgemäß berechnet wird nicht. Daher wird das Inhaltsfenster wird zu klein oder groß im Vergleich zu die hosting-Benutzeroberfläche, die leere Bereich bzw. die Clipping führt.

#### <a name="drag--drop"></a>Drag & drop
Jedes Mal, wenn konnte im gemischten Modus DPI-Wert-Szenarien (z. B. verschiedene Elemente der Benutzeroberfläche Rendern in verschiedenen Modi der DPI-Informationen), Drag & Drop Koordinaten Ziehpunktwerte werden in das endgültige Löschen Position am Ende falsche resultierende.

#### <a name="out-of-process-ui"></a>Out-of-Process-Benutzeroberfläche
Einige Elemente der Benutzeroberfläche Out-of-Process erstellt, und ist der Erstellen von externe Prozess in einem anderen DPI-Awareness-Modus als Visual Studio, kann dies die vorherigen Rendering-Probleme führen.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Windows Forms-Steuerelemente, Bilder oder Layouts, die nicht ordnungsgemäß gerendert
Nicht alle von der Windows Forms-Inhalten unterstützen PMA-Modus. Daher möglicherweise rendering-Problem mit falschen Layouts oder Skalierung angezeigt. Eine mögliche Lösung in diesem Fall ist, um Windows Forms-Inhalt in "System kennen" DpiAwarenessContext explizit zu rendern (finden Sie unter [erzwingen ein Steuerelement in einem bestimmten DpiAwarenessContext](#forcing-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms-Steuerelemente oder Windows, die nicht angezeigt.
Eine der Hauptursachen für dieses Problem, dass ist Entwickler, die ein Steuerelement oder das Fenster mit einem DpiAwarenessContext für ein Fenster mit einer anderen DpiAwarenessContext Neuzuordnen des übergeordneten Elements.

Die folgenden Abbildungen zeigen die aktuelle **Standard** Windows-Betriebssystem-Einschränkungen in überordnen von Windows:

![Ein Screenshot, der das richtige übergeordnete Verhalten](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

> [!Note]
> Sie können dieses Verhalten ändern, indem das Thread-Hosting-Verhalten festlegen (finden Sie unter [DpiHostinBehaviour](https://docs.microsoft.com/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Wenn Sie eine über-/ unterordnungsbeziehung zwischen den nicht unterstützten Modi festgelegt, daher es schlägt fehl, und das Steuerelement oder das Fenster kann nicht gerendert werden wie erwartet.

### <a name="diagnosing-issues"></a>Diagnostizieren von Problemen
Es gibt viele Faktoren berücksichtigt werden, wenn PMA-bezogene Probleme zu identifizieren: 

1. Unterstützt die Benutzeroberfläche oder logische erwarten, dass API oder Device-Werte.
    - WPF-UI und APIs in der Regel verwenden Sie logische Werte (aber nicht immer)
    - Win32-Benutzeroberfläche und APIs in der Regel verwenden Gerät Werte

2. Wo sind die Werte stammen?
    - Wenn die Werte von anderen-Benutzeroberfläche oder-API empfangen werden kann, ist es übergeben-Gerät oder logische Werte.
    - Wenn die Werte aus mehreren Quellen empfangen werden, werden alle verwenden/voraussichtlich die gleichen Typen von Werten oder müssen Konvertierungen kombiniert und angepasst werden?

3. Sind Sie UI-Konstanten verwendet und welche Form sind sie?

4. Ist der Thread im richtigen Kontext DPI-Wert für die Werte erhält es?
    - Die Änderungen zu gemischten DPI-hosting Codepfade in der Regel im entsprechenden Kontext platzieren, jedoch möglicherweise Arbeit außerhalb der main-Schleife oder ein Ereignis Nachrichtenfluss im falschen Kontext DPI durchgeführt werden.

5. Dass Werte DPI Kontextgrenzen überschreiten?
    - Drag & Drop ist eine gängige Situation, in denen Koordinaten DPI-Kontexten überschreiten. Fenster versucht, das richtige tun, aber in einigen Fällen der hostbenutzeroberfläche möglicherweise Konvertierung arbeiten, um sicherzustellen, dass übereinstimmende Kontextgrenzen.

### <a name="pma-nuget-package"></a>PMA NuGet-Paket
Die neuen DpiAwarness-Bibliotheken finden Sie auf die [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet-Paket.

### <a name="recommended-tools"></a>Empfohlene tools
Die folgenden Tools können einige der in den verschiedenen UI-Stapeln von Visual Studio unterstützt PMA-bezogene Probleme zu debuggen.

#### <a name="snoop"></a>-Snoop
Snoop ist ein XAML-Debugtool, die einige zusätzliche Funktionen, die die integrierte Visual Studio-XAML-Tools verfügt nicht über. Darüber hinaus muss Snoop nicht aktiv Debuggen von Visual Studio zum Anzeigen und Optimieren der WPF-UI sein. Die zwei Hauptverfahren, Snoop zum Diagnostizieren von Problemen mit PMA nützlich sein kann, ist für die Überprüfung der Koordinaten der logische Position oder Größe Grenzen und zum Überprüfen der Benutzeroberfläche der richtigen DPI-Wert verfügt.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio-XAML-tools
Wie Snoop können die XAML-Tools in Visual Studio PMA Probleme zu diagnostizieren. Wenn eine mögliche Ursache gefunden wurde, können Sie Haltepunkte festlegen und verwenden das Fenster "visuelle Echtzeitstruktur" als auch für die Debug-Fenster, um UI-Grenzen und aktuelle DPI-Werte zu überprüfen.

## <a name="strategies-for-fixing-pma-issues"></a>Strategien zum Beheben von Problemen mit PMA
### <a name="replacing-dpihelper-calls"></a>Ersatz der Aufrufe der DpiHelper
In den meisten Fällen beheben Probleme mit der Benutzeroberfläche in PMA Modus läuft Ersatz der Aufrufe in verwaltetem Code auf das alte *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* und *Microsoft.VisualStudio.PlatformUI.DpiHelper*Klassen, die durch Aufrufe der neuen *Microsoft.VisualStudio.Utilities.DpiAwareness* Helper-Klasse. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Für nativen Code wird es gelten, und Ersetzen Sie dabei Aufrufe an die alte *VsUI::CDpiHelper* Klasse durch Aufrufe der neuen *VsUI::CDpiAwareness* Klasse. 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

Die neuen Klassen DpiAwareness und CDpiAwareness bieten derselben Einheit Konvertierung Hilfsprogramme wie die Klassen DpiHelper aber einen zusätzlichen Eingabeparameter erfordern: das Benutzeroberflächenelement, das als Referenz für den Konvertierungsvorgang zu verwenden. Es ist wichtig zu beachten, dass die Skalierung Image-Hilfsprogramme in die neue DpiAwareness/CDpiAwareness-Hilfsprogramme, nicht vorhanden sind und bei Bedarf die [ImageService](https://docs.microsoft.com/visualstudio/extensibility/image-service-and-catalog?view=vs-2019) sollte stattdessen verwendet werden.

Die verwaltete DpiAwareness-Klasse bietet Hilfsprogramme für WPF und visuellen Elementen, Windows Forms-Steuerelemente und Win32-HWNDs HMONITORs (beide in Form von IntPtrs), während die native CDpiAwareness-Klasse bietet HWND und HMONITOR Hilfsprogramme.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms-Dialogfeldern, Windows oder Steuerelemente, die in der falschen DpiAwarenessContext angezeigt
Auch nach einer erfolgreichen überordnen von Windows mit anderen DpiAwarenessContexts (aufgrund von Windows-Standardverhalten), werden von Benutzern unter Umständen weiterhin Skalierung Probleme unter Windows mit anderen DpiAwarenessContexts Skalierung anders, angezeigt. Daher können Benutzer finden Sie unter Ausrichtung/verschwommenen Text oder Bild-Problemen auf der Benutzeroberfläche.

Die Lösung besteht darin, den richtigen Bereich DpiAwarenessContext für alle Fenster und Steuerelemente in der Anwendung festgelegt.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Der obersten Ebene des gemischten Modus (TLMM)-Dialogfelder
Wenn Sie Fenster auf oberster Ebene, z. B. modale Dialogfelder zu erstellen, ist es wichtig, um sicherzustellen, dass der Thread im richtigen Zustand vor dem Fenster (und das Handle) erstellt wird. Der Thread kann in versetzt werden System Awareness durch Verwenden der CDpiScope-Hilfsmethode in systemeigenen oder verwaltet das Hilfsobjekt DpiAwareness.EnterDpiScope in. (TLMM sollte im Allgemeinen auf nicht-WPF-Dialoge/Windows verwendet werden.)

### <a name="child-level-mixed-mode-clmm"></a>Untergeordnete Gemischter Modus (CLMM)
Standardmäßig erhalten untergeordnete Fenster, den aktuellen Thread DPI Awareness Kontext ohne übergeordnetes Element erstellt, oder DPI Awareness-Kontext des übergeordneten Elements bei Erstellung mit einem übergeordneten Element. Um ein untergeordnetes Element mit einem anderen DPI-Awareness-Kontext als das übergeordnete Objekt zu erstellen, kann der Thread in den gewünschten DPI-Awareness-Kontext abgelegt werden. Klicken Sie dann kann ohne übergeordnetes Element das untergeordnete Element erstellt und werden manuell erneut übergeordnet, für das übergeordnete Fenster.

#### <a name="clmm-issues"></a>CLMM-Probleme
Die meisten der Aufgaben des UI-Berechnung, die als Teil der wichtigsten messaging-Schleife oder ein Ereignis Kette vorgenommen wird, müssen bereits in den richtigen Kontext der DPI-Unterstützung ausgeführt werden. Aber wenn Koordinate oder größenanpassung Berechnungen außerhalb dieser main Workflows fertig sind, (z. B. während eines Tasks für die Zeit im Leerlauf oder außerhalb des Benutzeroberflächenthreads, klicken Sie dann der aktuelle Kontext der DPI-Awareness falsch führt zum Verlust der Benutzeroberfläche oder die falsch größenanpassung Probleme sein kann. Platzieren den Thread in den richtigen Zustand für die Benutzeroberfläche arbeiten in der Regel das Problem behebt.
 
#### <a name="opting-out-of-clmm"></a>Deaktivierung der CLMM
Wenn ein nicht-WPF-Toolfenster um eine vollständige PMA Unterstützung migriert wird, müssen sie CLMM deaktivieren. Zu diesem Zweck muss eine neue Schnittstelle implementiert werden: IVsDpiAware.

C#:

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```
 
C++:

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Für verwaltete Sprachen, ist der beste Ort für diese Schnittstelle implementieren, in der gleichen Klasse, die von abgeleitet *Microsoft.VisualStudio.Shell.ToolWindowPane*. Für C++, der idealen Speicherort für diese Schnittstelle implementieren, ist in der gleichen Klasse, die implementiert *IVsWindowPane* aus vsshell.h.

Der Wert, der durch die Mode-Eigenschaft zurückgegeben wird, über die Schnittstelle ist eine __VSDPIMODE (und Umwandlung in Uint in verwaltete):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Bedeutet, dass, die das Toolfenster, 96 DPI behandeln muss, behandelt Windows, skalieren sie für alle anderen DPI-Werte. Was für Inhalte wird etwas verschwommen.
- System bedeutet, dass, die das Toolfenster der DPI-Wert für die primäre behandeln muss, anzeigen DPI-Wert. Eine beliebige Anzeige mit einem übereinstimmenden DPI-Wert wird in der schärfer aussehen, aber wenn der DPI-Wert unterscheidet sich oder während der Sitzung geändert werden, Windows übernimmt die Skalierung, und es etwas verschwommen.
- PerMonitor bedeutet, dass das Toolfenster muss alle DPI-Werte auf allen Monitoren zu behandeln und jedes Mal, wenn der DPI-Wert ändert.

> [!NOTE]
> Visual Studio unterstützt nur PerMonitorV2-Awareness können, damit der PerMonitor Enum-Wert in der Windows-Wert, der DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 übersetzt.

#### <a name="forcing-a-control-into-a-specific-dpiawarenesscontext"></a>Erzwingen ein Steuerelement in einem bestimmten DpiAwarenessContext
Legacy-Benutzeroberfläche, die zur Unterstützung von PMA-Modus nicht aktualisiert werden möglicherweise immer noch kleine Änderungen an der arbeiten, während Visual Studio im PMA-Modus ausgeführt wird. Eine solche Lösung umfasst, um sicherzustellen, dass die Benutzeroberfläche in der richtigen DpiAwarenessContext erstellt wird. Um die Benutzeroberfläche in einem bestimmten DpiAwarenessContext zu erzwingen, können Sie einen Bereich DPI-Wert, durch den folgenden Code eingeben:

C#:

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

C++:

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Erzwingen der DpiAwarenessContext kann nur für nicht - WPF-UI und WPF-Dialogfeldern, die obersten Ebene. Wenn WPF-UI zu erstellen, ist in Toolfenstern oder Designer, gehostet werden, sobald der Inhalt in der WPF-UI-Struktur eingefügt wird, ruft sie in den aktuellen Prozess DpiAwarenessContext konvertiert.

## <a name="known-issues"></a>Bekannte Probleme
### <a name="windows-forms"></a>Windows Forms

Geändert, um die neuen gemischte Szenarien optimieren, Windows Forms wie erstellt sie Steuerelemente und Fenster ab, wenn ihr übergeordnetes Element nicht explizit festgelegt wurde. Früher verwendet Steuerelemente ohne explizite ein übergeordnetes Element einer internen "" Parken"Fenster" als temporäre übergeordnetes Element an das Steuerelement oder das Fenster erstellt wird. 

Vor .NET 4.8 gab es ein einzelnes "" Parken"Fenster", die die DpiAwarenessContext aus dem aktuellen Thread DPI-Awareness-Kontext zum Zeitpunkt der Erstellung des Fensters abruft. Jedes ohne übergeordnete Steuerelement erbt die gleichen DpiAwarenessContext wie das Fenster "Parken" auf, wenn das Handle des Steuerelements erstellt wird, und das dem übergeordneten endgültige/erwartet vom Anwendungsentwickler neu zugeordnet werden würde. Dies würde Timing-basierte Fehler auftreten, wenn das "" Parken"Fenster" eine höhere DpiAwarenessContext als das letzte übergeordnete Fenster hatte.

Ab .NET 4.8 gibt es jetzt eine "" Parken"Fenster" für jede DpiAwarenessContext, die gefunden wurde. Der andere Hauptunterschied ist, dass die für das Steuerelement verwendete DpiAwarenessContext zwischengespeichert werden, wenn das Steuerelement erstellt wird, nicht verwendet werden, wenn das Handle erstellt wird, an. Dies bedeutet das Gesamtverhalten der End ist identisch, jedoch kann aktivieren, was früher ein Problem Timing-basierte, ein Problem konsistent sein. Außerdem erhalten Entwickler der Anwendung weitere Deterministisches Verhalten für ihre UI-Code schreiben und Einschränken von es richtig.
