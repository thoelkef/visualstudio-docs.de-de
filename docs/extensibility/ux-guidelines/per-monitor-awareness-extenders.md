---
title: Unterstützung für die Erkennung von Visual Studio-Extendern pro Monitor
titleSuffix: ''
description: Erfahren Sie mehr über die neue extenderunterstützung für "pro Monitor", die in Visual Studio 2019 verfügbar ist.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: conceptual
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 2686248a087650f6170b72c8ef9b3a77e2ba275c
ms.sourcegitcommit: 6f3cf7a1bfc81a61f9a603461a1c34fd2221f100
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957353"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Unterstützung für die Erkennung von Visual Studio-Extendern pro Monitor

Bei Versionen vor Visual Studio 2019 war der dpi-Kontext des dpi-Kontexts auf "System fähig" festgelegt, anstatt eine dpi-Unterstützung pro Monitor zu erhalten. Das Ausführen von Systeminformationen führte zu einer beeinträchtigten visuellen Darstellung (z. b. unscharfe Schriftarten oder Symbolen), wenn Visual Studio über Monitore mit unterschiedlichen Skalierungsfaktoren hinweg gerengt werden musste oder Remote Computer mit unterschiedlichen Anzeige Konfigurationen (z. b. andere Windows-Skalierung).

Der dpi-Kontext von Visual Studio 2019 wird als "PMA" festgelegt, wenn die Umgebung dies unterstützt, sodass Visual Studio entsprechend der Konfiguration der Anzeige, in der es gehostet wird, und nicht in einer einzelnen vom System definierten Konfiguration dargestellt werden kann. Letztendlich Übersetzung in eine immer knackige Benutzeroberfläche für Oberflächenbereiche, die den PMA-Modus unterstützen.

Weitere Informationen zu den in diesem Dokument behandelten Begriffen und zum Gesamtszenario finden Sie in der Dokumentation zur [Entwicklung von Desktop Anwendungen in High dpi](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) .

## <a name="quickstart"></a>Schnellstart

- Stellen Sie sicher, dass Visual Studio im PMA-Modus ausgeführt wird (siehe **Aktivieren von PMA**)

- Überprüfen Sie, ob die Erweiterung für eine Reihe allgemeiner Szenarien ordnungsgemäß funktioniert (Weitere Informationen finden Sie unter **Testen der Erweiterungen für**"

- Wenn Sie Probleme finden, können Sie die in diesem Dokument erläuterten Strategien/Empfehlungen verwenden, um diese Probleme zu diagnostizieren und zu beheben. Außerdem müssen Sie das neue nuget-Paket " [Microsoft. VisualStudio. dpiawareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) " zu Ihrem Projekt hinzufügen, um auf die erforderlichen APIs zuzugreifen.

## <a name="enable-pma"></a>Aktivieren von PMA

Zum Aktivieren von "PMA" in Visual Studio müssen die folgenden Anforderungen erfüllt sein:

- Windows 10 April 2018-Update (v1803, RS4) oder höher
- .NET Framework 4,8 RTM oder höher
- Visual Studio 2019 mit aktivierter Option ["Rendering für Bildschirme mit unterschiedlichen Pixel dichten optimieren"](../../ide/reference/general-environment-options-dialog-box.md) aktiviert

Wenn diese Anforderungen erfüllt sind, aktiviert Visual Studio automatisch den PMA-Modus im gesamten Prozess.

> [!NOTE]
> Windows Forms Inhalt in Visual Studio (z. b. Eigenschaften Browser) unterstützt nur "PMA", wenn Sie Visual Studio 2019, Version 16,1 oder höher, verwenden.

## <a name="test-your-extensions-for-pma-issues"></a>Testen der Erweiterungen für "PMA"-Probleme

Visual Studio unterstützt offiziell die Benutzeroberflächen-Frameworks WPF, Windows Forms, Win32 und HTML/js. Wenn Visual Studio in den PMA-Modus versetzt wird, verhält sich jeder UI-Stapel anders. Daher wird unabhängig vom UI-Framework empfohlen, dass ein Test Durchlauf durchgeführt wird, um sicherzustellen, dass die gesamte Benutzeroberfläche mit dem Modus "PMA" kompatibel ist.

Es wird empfohlen, die folgenden allgemeinen Szenarien zu überprüfen:

- Ändern des Skalierungsfaktors einer einzelnen Monitor Umgebung, während die Anwendung ausgeführt wird.

  In diesem Szenario wird getestet, ob die Benutzeroberfläche auf die dynamische Windows-dpi-Änderung antwortet.

- Andocken/Andocken eines Laptops, bei dem ein angefügter Monitor auf den primären festgelegt ist und der angefügte Monitor einen anderen Skalierungsfaktor als der Laptop hat, während die Anwendung ausgeführt wird.

  In diesem Szenario wird getestet, ob die Benutzeroberfläche auf die Änderung der dpi-Änderung antwortet und wie die Behandlung von dynamisch hinzugefügt oder entfernt wird.

- Das vorhanden sein mehrerer Monitore mit unterschiedlichen Skalierungsfaktoren und die Verschiebung der Anwendung zwischen diesen.

  In diesem Szenario wird getestet, ob die Benutzeroberfläche auf die Anzeige dpi-Änderung antwortet.
    
- Remoting zu einem Computer, wenn der lokale Computer und der Remote Computer über unterschiedliche Skalierungsfaktoren für den primären Monitor verfügen.

  In diesem Szenario wird getestet, ob die Benutzeroberfläche auf die dynamische Windows-dpi-Änderung antwortet.

Ein guter vorläufiger Test für die Frage, ob Ihre Benutzeroberfläche Probleme haben kann, ist, ob der Code die Klassen *Microsoft. VisualStudio. Utilities. dpi. dpihelper*, *Microsoft. VisualStudio. PlatformUI. dpihelper*oder *vsui:: cdpihelper* verwendet. Diese alten dpihelper-Klassen unterstützen nur das System-dpi-Bewusstsein und funktionieren nicht immer ordnungsgemäß, wenn der Prozess "PMA" ist

Die typische Verwendung dieser dpihilfsprogramme sieht wie folgt aus:

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

Im vorherigen Beispiel wird ein Rechteck, das die logischen Begrenzungen eines Fensters darstellt, in Geräte Einheiten konvertiert, sodass es an die systemeigene Methode "MonitorFromPoint", die Geräte Koordinaten erwartet, zum Zurückgeben eines exakten Monitor Zeigers übermittelt werden kann.

### <a name="classes-of-issues"></a>Klassen von Problemen
Wenn der Modus "PMA" für Visual Studio aktiviert ist, kann die Benutzeroberfläche Probleme auf verschiedene Weise replizieren. Die meisten dieser Probleme können in beliebigen Visual Studio-unterstützten Benutzeroberflächen-Frameworks auftreten. Darüber hinaus können diese Probleme auch auftreten, wenn ein Teil der Benutzeroberfläche in dpi-Skalierungs Szenarios im gemischten Modus gehostet wird (Weitere Informationen finden Sie in der Windows- [Dokumentation](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) ). 

#### <a name="win32-window-creation"></a>Win32-Fenster Erstellung
Beim Erstellen von Fenstern mit "kreatewindow ()" oder "kreatewindowex ()" ist ein gängiges Muster, das Fenster an Koordinaten (0,0) (die obere/linke Ecke der primären Anzeige) zu erstellen und dann an die endgültige Position zu verschieben. Dies kann jedoch dazu führen, dass das Fenster eine von dpi geänderte Nachricht oder ein Ereignis auslöst, das andere UI-Nachrichten oder-Ereignisse erneut auslösen kann und schließlich zu nicht gewünschtem Verhalten oder Rendering führt.

#### <a name="wpf-element-placement"></a>Platzierung von WPF-Elementen
Beim Verschieben von WPF-Elementen mithilfe der alten Microsoft. VisualStudio. Utilities. dpi. dpihelper-Elemente werden die oberen linken Koordinaten möglicherweise nicht ordnungsgemäß berechnet, wenn Elemente sich auf einem nicht primären dpi-Wert befinden.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialisierung von Benutzeroberflächen-Element Größen oder-Positionen
Wenn die Größe oder Position der Benutzeroberfläche (wenn Sie als Geräte Einheiten gespeichert sind) in einem anderen dpi-Kontext wieder hergestellt wird, als Sie in gespeichert wurde, wird Sie nicht ordnungsgemäß positioniert und verkleinert. Dies liegt daran, dass Geräte Einheiten über eine inhärente dpi-Beziehung verfügen.

#### <a name="incorrect-scaling"></a>Falsche Skalierung
Benutzeroberflächen Elemente, die auf dem primären dpi erstellt werden, werden korrekt skaliert. Wenn Sie jedoch in eine Anzeige mit einem anderen dpi-Wert verschoben werden, werden Sie nicht neu skaliert, und ihr Inhalt ist zu groß oder zu klein.

#### <a name="incorrect-bounding"></a>Falsche Begrenzungs Zeichen
Ebenso wie das Skalierungs Problem berechnen Benutzeroberflächen Elemente ihre Grenzen in Ihrem primären dpi-Kontext ordnungsgemäß, wenn Sie jedoch auf einen nicht primären dpi-dpi verschoben werden, werden die neuen Begrenzungen nicht ordnungsgemäß berechnet. Daher ist das Inhalts Fenster im Vergleich zur hostingbenutzeroberfläche zu klein oder zu groß, was zu einem leeren Bereich oder Clipping führt.

#### <a name="drag--drop"></a>Drag & Drop
Bei dpi-Szenarios im gemischten Modus (z. b. unterschiedliche Benutzeroberflächen Elemente, die in verschiedenen dpi-Informationen gerendert werden) können Drag & Drop-Koordinaten falsch berechnet werden, was dazu führt, dass die endgültige Ablage Position falsch ist.

#### <a name="out-of-process-ui"></a>Out-of-Process-Benutzeroberfläche
Einige Benutzeroberflächen werden außerhalb des Prozesses erstellt, und wenn sich der erstellte externe Prozess in einem anderen dpi-Awareness-Modus als Visual Studio befindet, kann dies zu den vorherigen Renderingproblemen führen.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Falsch gerenderte Windows Forms Steuerelemente, Bilder oder Layouts
Der PMA-Modus wird nicht von allen Windows Forms Inhalt unterstützt. Daher wird möglicherweise ein Renderingproblem mit falschen Layouts oder der Skalierung angezeigt. Eine mögliche Lösung besteht in diesem Fall darin, Windows Forms Inhalt in "System Aware" dpiawareress Context explizit zu Rendering (Weitere Informationen finden Sie unter [Erzwingen eines Steuer Elements in einem bestimmten dpiawartestercontext](#force-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms Steuerelemente oder Fenster, die nicht angezeigt werden
Eine der Hauptgründe für dieses Problem sind Entwickler, die versuchen, ein Steuerelement oder ein Fenster mit einem dpiawareness Context einem Fenster mit einem anderen dpiawareness Context-Element neu zu zuordnen.

Die folgenden Abbildungen zeigen die aktuellen **Standard** Einschränkungen des Windows-Betriebssystems bei der untergeordneten Windows-Betriebssystem-

![Screenshot des korrekten Verhaltens Verhaltens](media/PMA-parenting-behavior.PNG)

> [!Note]
> Sie können dieses Verhalten ändern, indem Sie das Verhalten des Thread Hostings festlegen (siehe [Dpi_Hosting_Behavior-Enumeration](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Wenn Sie daher die Beziehung zwischen über-und untergeordneten Elementen zwischen nicht unterstützten Modi festlegen, tritt ein Fehler auf, und das Steuerelement oder Fenster wird möglicherweise nicht wie erwartet gerendert.

### <a name="diagnose-issues"></a>Diagnostizieren von Problemen

Bei der Identifizierung von PMA-bezogenen Problemen müssen viele Faktoren berücksichtigt werden: 

- Erwartet die Benutzeroberfläche oder API logische oder Geräte Werte?
    - WPF-Benutzeroberfläche und APIs verwenden normalerweise logische Werte (aber nicht immer).
    - Win32-Benutzeroberfläche und APIs verwenden normalerweise Geräte Werte

- Wo sind die Werte, die aus stammen?
    - Wenn Werte von einer anderen Benutzeroberfläche oder API empfangen werden, übergibt Sie die Geräte-oder logischen Werte.
    - Wenn Sie Werte aus mehreren Quellen erhalten, verwenden Sie alle die gleichen Werttypen bzw. erwarten Sie, dass Konvertierungen gemischt und abgeglichen werden müssen?

- Werden Benutzeroberflächen Konstanten verwendet, und in welchem Formular befinden Sie sich?

- Befindet sich der Thread im richtigen dpi-Kontext für die empfangenen Werte?

  Die Änderungen zum Aktivieren des gemischten dpi-Hostings sollten im allgemeinen Codepfade im richtigen Kontext platzieren, aber die Arbeit außerhalb der Hauptnachrichten Schleife oder des Ereignis Flusses kann im falschen dpi-Kontext ausgeführt werden.

- Überschreiten Werte für dpi-Kontext Grenzen?

  Drag & Drop ist eine gängige Situation, in der Koordinaten Kontext übergreifende dpi-Kontexte aufweisen können. Das Fenster versucht, das richtige zu tun, aber in einigen Fällen muss die Host Benutzeroberfläche möglicherweise Konvertierungs Aufgaben durchführen, um übereinstimmende Kontext Grenzen sicherzustellen.

### <a name="pma-nuget-package"></a>PMA-nuget-Paket
Die neuen dpiawarness-Bibliotheken finden Sie im nuget-Paket " [Microsoft. VisualStudio. dpiawareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) ".

### <a name="recommended-tools"></a>Empfohlene Tools
Die folgenden Tools helfen Ihnen beim Debuggen von PMA-bezogenen Problemen in einigen der verschiedenen von Visual Studio unterstützten Benutzeroberflächen stapeln.

#### <a name="snoop"></a>Snoop
Snoop ist ein XAML-Debugtool mit zusätzlichen Funktionen, die die integrierten Visual Studio XAML-Tools nicht haben. Außerdem muss von Snoop kein aktives Debuggen von Visual Studio durchführt werden, um die WPF-Benutzeroberfläche anzeigen und optimieren zu können. Die zwei Hauptmethoden, mit denen snoop bei der Diagnose von PMA-Problemen nützlich sein kann, ist das Überprüfen logischer Platzierungskoordinaten oder der Größenbegrenzungen und die Validierung der Benutzeroberfläche mit dem richtigen dpi-Wert.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio-XAML-Tools
Wie bei snoop können die XAML-Tools in Visual Studio bei der Diagnose von PMA-Problemen helfen. Sobald ein wahrscheinlichste Fehler gefunden wird, können Sie Haltepunkte festlegen und sowohl das visuelle Fenster der visuellen Struktur als auch die Debuggingfenster verwenden, um die Benutzeroberflächen Begrenzungen und den aktuellen dpi-Wert zu überprüfen.

## <a name="strategies-for-fixing-pma-issues"></a>Strategien zum Beheben von PMA-Problemen

### <a name="replace-dpihelper-calls"></a>Ersetzen von dpihelper-aufrufen

In den meisten Fällen kann das Beheben von Problemen mit der Benutzeroberfläche im PMA-Modus dazu geführt werden, Aufrufe in verwaltetem Code durch Aufrufe der neuen *Klasse "Microsoft. VisualStudio. Utilities. dpi. dpihelper* " und " *Microsoft. VisualStudio. PlatformUI. dpihelper* *" zu ersetzen. Microsoft. VisualStudio. Utilities. dpiawareness* -Hilfsklasse. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Bei nativem Code werden Aufrufe der alten *vsui:: cdpihelper* -Klasse durch Aufrufe der neuen *vsui:: cdpiawareness* -Klasse ersetzt. 

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

Die neuen Klassen dpiawareness und cdpiawareness bieten dieselben Einheiten Konvertierungs Hilfen wie die dpihelper-Klassen, erfordern jedoch einen zusätzlichen Eingabeparameter: das UI-Element, das als Verweis für den Konvertierungs Vorgang verwendet werden soll. Beachten Sie, dass die Abbild-Skalierungs Hilfen nicht in den neuen dpiawareness/cdpiawareness-Hilfsprogramme vorhanden sind. Falls erforderlich, sollte stattdessen der [ImageService](../image-service-and-catalog.md) verwendet werden.

Die verwaltete dpiawareness-Klasse bietet Hilfsprogramme für WPF-Visualisierungen, Windows Forms Steuerelemente und Win32-HWNDs und hmonitors (beide in Form von intptrs), während die native cdpiawareness-Klasse HWND-und Hmonitor-Hilfsprogramme bietet.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms Dialogfelder, Fenster oder Steuerelemente, die im falschen dpiawareress Context angezeigt werden.
Auch nach einem erfolgreichen übernehmen von Fenstern mit unterschiedlichen dpiawardeesskontexte (aufgrund des Standard Verhaltens von Windows) können Benutzer Skalierungsprobleme weiterhin erkennen, wenn Windows mit unterschiedlichen dpiawarteesskontexte unterschiedlich skaliert wird. Folglich können Benutzer auf der Benutzeroberfläche Probleme mit der Ausrichtung/Unschärfe oder dem Bild erkennen.

Die Lösung besteht darin, den korrekten dpiawareness Context-Bereich für alle Fenster und Steuerelemente in der Anwendung festzulegen.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Dialogfelder im gemischten Modus (tlmm) der obersten Ebene
Beim Erstellen von Fenstern der obersten Ebene, z. b. modale Dialogfelder, ist es wichtig, sicherzustellen, dass sich der Thread im richtigen Zustand befindet, bevor das Fenster (und dessen Handle) erstellt wird. Der Thread kann mithilfe des cdpiscope-Hilfsprogramms in nativem oder dem Hilfsprogramm dpiawareness. enterdpiscope in verwaltet in das System Bewusstsein versetzt werden. (Tlmm sollte in der Regel in nicht-WPF-Dialogfeldern/-Fenstern verwendet werden.)

### <a name="child-level-mixed-mode-clmm"></a>Gemischter Modus auf untergeordneter Ebene (clmm)
Standardmäßig empfangen untergeordnete Fenster den Kontext des aktuellen Thread-dpi-Kontexts, wenn er ohne ein übergeordnetes Element erstellt wurde Zum Erstellen eines untergeordneten Elements mit einem anderen dpi-Kontext als dem übergeordneten Kontext kann der Thread in den gewünschten Kontext für den dpi-Wert eingefügt werden. Anschließend kann das untergeordnete Element ohne ein übergeordnetes Element erstellt und manuell dem übergeordneten Fenster neu zugeordnet werden.

#### <a name="clmm-issues"></a>Clmm-Probleme
Die meisten Benutzeroberflächen Berechnungen, die als Teil der Haupt-Messaging Schleife oder-Ereigniskette ausgeführt werden, sollten bereits im richtigen dpi-Kontext ausgeführt werden. Wenn jedoch Koordinaten-oder größenberechnungen außerhalb der Haupt Workflows vorgenommen werden (z. b. während einer Leerlaufzeit Aufgabe oder außerhalb des UI-Threads), ist der aktuelle dpi-Kontext möglicherweise falsch, was zu Problemen mit der Benutzeroberflächen-oder fehlerhafter Größenänderung führt. Wenn Sie den Thread in den richtigen Zustand für die UI-Arbeit versetzen, wird das Problem in der Regel behoben.
 
#### <a name="opt-out-of-clmm"></a>Ablehnen von clmm
Wenn ein nicht-WPF-Tool Fenster zur vollständigen Unterstützung von PMA migriert wird, muss es sich gegen clmm entscheiden. Zu diesem Zweck muss eine neue Schnittstelle implementiert werden: IVsDpiAware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Bei verwalteten Sprachen ist der beste Ort für die Implementierung dieser Schnittstelle die gleiche Klasse, die von *Microsoft. VisualStudio. Shell. ToolWindowPane*abgeleitet wird. Für C++ist der beste Ort für die Implementierung dieser Schnittstelle die gleiche Klasse, die *IVsWindowPane* aus vsshell. h implementiert.

Der Wert, der von der Eigenschaft "Mode" für die Schnittstelle zurückgegeben wird, ist eine __VSDPIMODE (und wird in eine uint in Managed umgewandelt):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Wenn Sie nicht wissen, dass das Tool Fenster 96 dpi verarbeiten muss, wird es von Windows für alle anderen DPIs skaliert. Der Inhalt ist leicht verschwommen.
- System bedeutet, dass das Tool Fenster den dpi-Code für die primäre Anzeige dpi verarbeiten muss. Jede Anzeige mit einem übereinstimmenden dpi-Wert sieht kurz aus, aber wenn sich der dpi-Wert unterscheidet oder während der Sitzung geändert wird, wird die Skalierung von Windows verarbeitet, und die Skalierung ist leicht verschwommen.
- Permonitor bedeutet, dass das Tool Fenster alle DPIs in allen anzeigen und bei jeder Änderung des dpi-Punkts verarbeiten muss.

> [!NOTE]
> Visual Studio unterstützt nur PerMonitorV2 Awareness, sodass der permonitor-Enumerationswert in den Windows-Wert von DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 übersetzt wird.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Erzwingen eines Steuer Elements in einem bestimmten dpiawareress Context

Die Legacy-Benutzeroberfläche, die nicht zur Unterstützung des PMA-Modus aktualisiert wird, benötigt möglicherweise trotzdem kleinere Anpassungen, damit Sie funktionieren, während Visual Studio im PMA-Modus ausgeführt wird. Eine solche Korrektur besteht darin, sicherzustellen, dass die Benutzeroberfläche im rechten dpiawareress context erstellt wird. Sie können einen dpi-Bereich mit folgendem Code eingeben, um die Benutzeroberfläche in einem bestimmten dpiawareress Context zu erzwingen:

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Das Erzwingen von dpiawareress Context funktioniert nur für WPF-Benutzeroberflächen und WPF-Dialogfelder auf oberster Ebene. Wenn Sie die WPF-Benutzeroberfläche erstellen, die in Tool Fenstern oder Designern gehostet werden soll, sobald der Inhalt in die WPF-Benutzeroberflächen Struktur eingefügt wurde, wird er in den aktuellen Prozess dpiawaresesscontext konvertiert.

## <a name="known-issues"></a>Bekannte Probleme

### <a name="windows-forms"></a>Windows Forms

Um die neuen Szenarios im gemischten Modus zu optimieren, Windows Forms geändert, wie Steuerelemente und Fenster erstellt werden, wenn Ihr übergeordnetes Element nicht explizit festgelegt wurde. Früher verwendeten Steuerelemente ohne explizites übergeordnetes Element ein internes "Park Fenster" als temporäres übergeordnetes Element für das Steuerelement oder das Fenster, das erstellt wird. 

Vor .NET 4,8 gab es ein einzelnes "Park Fenster", das seinen "dpiawareness Context" aus dem aktuellen Thread-dpi-Kontext zum Erstellungs Zeitpunkt des Fensters abruft. Jedes nicht übergeordnete Steuerelement erbt denselben dpiawareness Context wie das Fenster "Parking", wenn das Handle des Steuer Elements erstellt wird, und würde dem endgültigen bzw. erwarteten übergeordneten Element vom Anwendungsentwickler neu zugeordnet werden. Dies würde zu Zeit Steuerungs Fehlern führen, wenn für das Fenster "Fenster" ein höheres "dpiawareness Context" als das endgültige übergeordnete Fenster fest steht.

Ab .NET 4,8 gibt es jetzt ein "Park Fenster" für jeden gefundenen dpiawareness Context. Der andere Hauptunterschied besteht darin, dass der für das Steuerelement verwendete dpiawareress Context zwischengespeichert wird, wenn das Steuerelement erstellt wird, und nicht, wenn das Handle erstellt wird. Dies bedeutet, dass das gesamte End-Verhalten identisch ist, aber auch das, was als Zeit Punkt basiertes Problem verwendet wurde, in ein konsistentes Problem umwandeln kann. Außerdem erhält der Anwendungsentwickler ein besser deterministisches Verhalten beim Schreiben Ihres UI-Codes und der ordnungsgemäßen Bereichs Einschränkung.
