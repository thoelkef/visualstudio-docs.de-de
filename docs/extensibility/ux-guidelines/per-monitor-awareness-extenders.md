---
title: Unterstützung für die Monitorspezifische dpi-Erkennung für Visual Studio-Extender
titleSuffix: ''
description: Erfahren Sie, bis die neue Extender-Unterstützung für pro-Monitor-Unterstützung in Visual Studio-2019 verfügbar.
ms.date: 04/09/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 42de73a29e053066c0fbeca72ca3511b58b2fa7e
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477681"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Unterstützung für die Monitorspezifische dpi-Erkennung für Visual Studio-Extender

Versionen vor Visual Studio-2019 mussten kontextabhängig Awareness DPI-Wert, auf dem System kennen, anstatt eine monitorspezifische dpi--DPI-bewusst (PMA) festgelegt. Im System Awareness geführt haben ausführen in einer beeinträchtigten visuelle Darstellung (z. B. unscharf Schriftarten oder Symbolsatz) jedes Mal, wenn Visual Studio über Monitore mit verschiedenen Skalierungsfaktoren gerendert musste oder eine Remoteverbindung mit andere Konfigurationen (z. B. verschiedene Computer Windows-Skalierung).

Der DPI-Wert-Awareness-Kontext von Visual Studio-2019 ist Satz als monitorspezifische DPI-bewusst, sodass Visual Studio entsprechend der Konfiguration der Anzeige gerendert, wo sie gehostet wird, anstatt eine generische System definierten Konfiguration. In eine scharfe Benutzeroberfläche für Oberflächen übersetzen, die Unterstützung für PMA implementieren letztlich.

Finden Sie in der [hohe DPI-Wert Desktop-Anwendungsentwicklung unter Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) Dokumentation für Weitere Informationen über die Bedingungen und das allgemeine Szenario in diesem Dokument behandelt.

## <a name="quickstart"></a>Schnellstart
- Stellen Sie sicher, Visual Studio im PMA-Modus ausgeführt wird (siehe **PMA aktivieren**)

- Überprüfen Sie Ihre Erweiterung funktioniert ordnungsgemäß, auf eine Reihe von Szenarios (finden Sie unter **Testen Ihre Erweiterungen für PMA Probleme**)

- Wenn Sie Probleme feststellen, müssen Sie das neue PMA NuGet-Paket hinzufügen zu diagnostizieren und Beheben von Problemen mit der Strategien und Empfehlungen, die in diesem Dokument beschriebenen

## <a name="enabling-pma"></a>Aktivieren der PMA
Um PMA in Visual Studio zu aktivieren, müssen die folgenden Anforderungen erfüllt sein:
1)  Windows 10 April 2018 Update (Version RS4 v1803) oder höher
2)  .NET Framework 4.8 RTM oder höher (derzeit wird als eigenständige Vorschau oder Bundle mit aktuellen Windows Insider-builds)
3)  Visual Studio-2019 mit der ["Optimieren des Renderings für Bildschirme mit verschiedenen Pixel dichten"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) Option aktiviert ist

Wenn diese Anforderungen erfüllt sind, wird Visual Studio automatisch PMA über den Prozess aktiviert.

## <a name="testing-your-extensions-for-pma-issues"></a>Testen Ihre Erweiterungen für PMA-Probleme

Visual Studio unterstützt offiziell die WPF, Windows Forms, Win32- und HTML/JS-UI-Frameworks. Wenn Visual Studio in den PMA Modus versetzt wird, verhalten sich anders als die verschiedenen UI-Stapel. Aus diesem Grund wird unabhängig vom Benutzeroberflächen-Frameworks empfohlen, dass ein Testdurchlauf ausgeführt wird, um sicherzustellen, dass alle UI mit PMA kompatibel ist.

Unabhängig von der UI-Framework die Erweiterung unterstützt, es wird empfohlen, Sie die folgenden gängigen Szenarien überprüfen:

1. Den Skalierungsfaktor einer einzelnen Monitor Umgebung ändern, während die Anwendung ausgeführt wird. *
    - Dieses Szenario hilft dabei, testen, ob die Benutzeroberfläche reagiert auf die dynamische Windows-DPI-Änderung

2. Verankern und lösen hat ein Laptop, ein angeschlossenen Monitor auf dem primären und dem angeschlossenen Monitor festgelegt ist, einen andere Skalierungsfaktor als die primäre Datenbank aus, während die Anwendung ausgeführt wird.
    - Dieses Szenario hilft dabei, testen, ob die Benutzeroberfläche auf dem Bildschirm reagiert, DPI-Änderung sowie das Behandeln von zeigt dynamisch hinzugefügt oder entfernt wird

3. Müssen mehrere Monitore mit verschiedenen Skalierungsfaktor, und verschieben Sie die Anwendung zwischen ihnen.
    - Dieses Szenario hilft dabei, testen, ob die Benutzeroberfläche reagiert auf die Anzeige DPI-Änderung
    
4. Remoting auf einem Computer, wenn die lokale und remote-Computer andere Skalierungsfaktoren für den primären Monitor besitzen.
    - Dieses Szenario hilft dabei, testen, ob die Benutzeroberfläche reagiert auf die dynamische Windows-DPI-Änderung

Ein guter vorläufiger Test für gibt an, ob die Benutzeroberfläche Probleme möglicherweise ist, und zwar unabhängig davon, ob der Code entweder nutzt die *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* oder *Microsoft.VisualStudio.PlatformUI.DpiHelper* Klassen. Diese alten DpiHelper Klassen unterstützen nur die System-DPI-Unterstützung und wird nicht immer ordnungsgemäß, wenn der Prozess PMA ist.

Typische Verwendung der folgenden DpiHelpers sieht so aus wie:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

IntPtr monitor = NativeMethods.MonitorFromPoint(screenIntTopRight, NativeMethods.Monitor_DEFAULTTONEARST);
```

Im vorherigen Beispiel wird ein Rechteck, das die logischen Begrenzungen eines Fensters darstellt in Geräteeinheiten konvertiert, damit es an die systemeigene Methode MonitorFromPoint übergeben werden kann, die Gerätekoordinaten erwartet wird, um eine genaue Überwachung Zeiger zurückgegeben.

### <a name="classes-of-issues"></a>Klassen von Problemen

Wenn PMA für Visual Studio aktiviert ist, konnte von die Benutzeroberfläche Probleme auf verschiedene allgemeine Weise repliziert werden. Die meisten, wenn nicht alle möglich diese Probleme in einem der unterstützten Visual Studio-Benutzeroberflächen-Frameworks. Darüber hinaus diese Probleme können auftreten, auch wenn ein Element der Benutzeroberfläche im gemischten Modus-DPI-Skalierung Szenarien gehostet wird (finden Sie in der Windows [Dokumentation](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) Weitere). 

#### <a name="win32-window-creation"></a>Erstellen von Win32-Fenster
Wenn Sie Windows mit CreateWindow() oder CreateWindowEx() zu erstellen, wird ein allgemeines Muster zum Erstellen des Fensters an Koordinaten 0,0 (/ linken oberen Ecke der primären Anzeige), verschieben Sie ihn auf die letzte Position. Das Fenster zum Auslösen der DPI-Wert kann dazu führen, dass dies jedoch geändert, Nachricht oder des Ereignisses, die auch andere UI-Nachrichten oder Ereignisse erneut auslösen, und schließlich Rendering zu unerwünschtem Verhalten führen kann.

#### <a name="wpf-element-placement"></a>Platzierung der WPF-element
Beim Verschieben von WPF-Elemente, die mit der alten Microsoft.VisualStudio.Utilities.Dpi.DpiHelper möglicherweise Koordinaten der oberen linken nicht ordnungsgemäß berechnet werden, wenn Elemente im Fall zweit-DPI-Werte sind.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialisierung von UI-Element-Größe und Position
Wenn der UI-Größe oder Position, auf einem anderen DPI-Kontext wiederhergestellt wird als was sie am gespeichert wurde, wird positioniert und Größe nicht ordnungsgemäß. Dies geschieht, weil die logischen Begrenzungen eines Fensters in Geräteeinheiten konvertiert werden, so, dass es an die Win32-Methode MonitorFromPoint übergeben werden kann, die Gerätekoordinaten erwartet wird, um eine genaue Überwachung Zeiger zurückgegeben.

#### <a name="incorrect-scaling"></a>Falsche Skalierung
UI-Elemente, die auf den primären DPI-Wert erstellt werden ordnungsgemäß skaliert werden, jedoch beim Verschieben auf einen Monitor mit einer anderen DPI-Wert, sie nicht skalieren und daher ihren Inhalt im Endeffekt zu groß oder klein ist.

#### <a name="incorrect-bounding"></a>Falsche umgebenden
Auf ähnliche Weise für die Skalierung Problem berechnet Elemente der Benutzeroberfläche ihre Grenzen ordnungsgemäß auf ihrem primären DPI-Kontext, jedoch, wenn in einem nicht primären DPI verschoben, die neuen Grenzen ordnungsgemäß berechnet wird nicht. Daher wird das Inhaltsfenster wird zu klein oder groß im Vergleich zu die hosting-Benutzeroberfläche, die leere Bereich bzw. die Clipping führt.

#### <a name="drag--drop"></a>Drag & drop
Jedes Mal, wenn konnte im gemischten Modus DPI-Wert-Szenarien (z. B. verschiedene UI-Elemente beim Rendern im Kontext von sowohl primäre als auch nicht primären DPI-Wert), Drag & Drop Koordinaten Ziehpunktwerte werden in das endgültige Löschen Position am Ende falsche resultierende.

#### <a name="out-of-process-ui"></a>Out-of-Process-Benutzeroberfläche
Einige Elemente der Benutzeroberfläche Out-of-Process erstellt, und ist der Erstellen von externe Prozess in einem anderen DPI-Awareness-Modus als Visual Studio, kann dies die vorherigen Rendering-Probleme führen.

#### <a name="windows-forms-controls-images-or-windows-not-displaying"></a>Windows Forms-Steuerelemente, Bilder oder Windows nicht angezeigt.
Eine der Hauptursachen für dieses Problem, dass ist Entwickler, die ein Steuerelement oder das Fenster mit einem DpiAwarenessContext in ein anderes DpiAwarenessContext Fenster Neuzuordnen des übergeordneten Elements. 

Die folgenden Abbildungen zeigen die aktuellen Einschränkungen der Windows-Betriebssystem in überordnen von Windows, es sei denn, Thread-hosting Verhalten explizit geändert wird:

![Ein Screenshot, der das richtige übergeordnete Verhalten](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

Wenn Sie eine über-/ unterordnungsbeziehung zwischen den nicht unterstützten Modi festgelegt, daher es schlägt fehl, und das Steuerelement oder das Fenster kann nicht gerendert werden wie erwartet.

### <a name="diagnosing-issues"></a>Diagnostizieren von Problemen
Es gibt viele Faktoren berücksichtigt werden, wenn PMA-bezogene Probleme zu identifizieren: 

1. Ist die Benutzeroberfläche oder der API erwarteten logische oder Gerät-Werte.
    - WPF-UI und APIs in der Regel verwenden Sie logische Werte (aber nicht immer)
    - Win32-Benutzeroberfläche und APIs in der Regel verwenden Gerät Werte

2. Wo sind die Werte stammen?
    - Wenn die Werte von anderen-Benutzeroberfläche oder-API empfangen werden kann, ist es übergeben-Gerät oder logische Werte.
    - Wenn die Werte aus mehreren Quellen empfangen werden, werden alle verwenden/voraussichtlich die gleichen Typen von Werten oder müssen Konvertierungen kombiniert und angepasst werden?

3. Sind Sie UI-Konstanten verwendet und welche Form sind sie?

4. Ist der Thread im richtigen Kontext DPI-Wert für die Werte erhält es?
    - Die Änderungen zu CLMM Codepfade in der Regel im richtigen Kontext platzieren, jedoch möglicherweise Arbeit außerhalb der main-Schleife oder ein Ereignis Nachrichtenfluss im falschen Kontext DPI durchgeführt werden.

5. Dass Werte DPI Kontextgrenzen überschreiten?
    - Drag & Drop ist eine gängige Situation, in denen Koordinaten DPI-Kontexten überschreiten. Fenster versucht, das richtige tun, aber in einigen Fällen der hostbenutzeroberfläche möglicherweise Konvertierung arbeiten, um sicherzustellen, dass übereinstimmende Kontextgrenzen.

### <a name="pma-nugget-package"></a>PMA NuGet-Paket
Die neuen DpiAwarness-Bibliotheken finden Sie auf das Microsoft.VisualStudio.DpiAwareness NuGet-Paket.

### <a name="recommended-tools"></a>Empfohlene tools
Die folgenden Tools können einige der in den verschiedenen UI-Stapeln von Visual Studio unterstützt PMA-bezogene Probleme zu debuggen.

#### <a name="snoop"></a>-Snoop
Snoop ist ein XAML-Debugtool, die einige zusätzliche Funktionen, die die integrierte Visual Studio-XAML-Tools verfügt nicht über. Darüber hinaus muss Snoop nicht aktiv Debuggen von Visual Studio zum Anzeigen und Optimieren der WPF-UI sein. Die zwei Hauptverfahren, Snoop zum Diagnostizieren von Problemen mit PMA nützlich sein kann, ist für die Überprüfung der Koordinaten der logische Position oder Größe Grenzen und zum Überprüfen der Benutzeroberfläche der richtigen DPI-Wert verfügt.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio-XAML-tools
Wie Snoop können die XAML-Tools in Visual Studio PMA Probleme zu diagnostizieren. Wenn eine mögliche Ursache gefunden wurde, können Sie Haltepunkte festlegen und verwenden das Fenster "visuelle Echtzeitstruktur" als auch für die Debug-Fenster, um UI-Grenzen und aktuelle DPI-Werte zu überprüfen.

## <a name="strategies-for-fixing-pma-issues"></a>Strategien zum Beheben von Problemen mit PMA

### <a name="replacing-dpihelper-calls"></a>Ersatz der Aufrufe der DpiHelper
In den meisten Fällen macht das Beheben von PMA Ersatz der Aufrufe in verwaltetem Code auf das alte: *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* und *Microsoft.VisualStudio.PlatformUI.DpiHelper* Klassen, die durch Aufrufe der neuen *Microsoft.VisualStudio.Utilities.DpiAwareness* Helper-Klasse. 

Für nativen Code wird es gelten, und Ersetzen Sie dabei Aufrufe an die alte *VsUI::CDpiHelper* Klasse durch Aufrufe der neuen *VsUI::CDpiAwareness* Klasse. Die neuen Klassen DpiAwareness und CDpiAwareness bieten die gleiche Konvertierung-Hilfsprogramme aus, wie die Klassen DpiHelper aber einen zusätzlichen Eingabeparameter erfordern: das Benutzeroberflächenelement, das als Referenz für den Konvertierungsvorgang zu verwenden. 

Die verwaltete DpiAwareness-Klasse bietet Hilfsprogramme für WPF und visuellen Elementen, Windows Forms-Steuerelemente und Win32-HWNDs HMONITORs (beide in Form von IntPtrs), während die native CDpiAwareness-Klasse bietet HWND und HMONITOR Hilfsprogramme.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms-Dialogfeldern, Windows oder Steuerelemente, die in der falschen DpiAwarenessContext angezeigt
Auch nach einer erfolgreichen überordnen von Windows mit anderen DpiAwarenessContext (aufgrund von Windows-Standardverhalten), werden von Benutzern unter Umständen immer noch Probleme skalieren, wie verschiedene DpiAwarenessContext Windows unterschiedlich skalieren, angezeigt. Benutzern unter Umständen daher Ausrichtung/unscharf Text- oder Image-Probleme auf der Benutzeroberfläche angezeigt.

Die Lösung besteht darin, den richtigen Bereich DpiAwarenessContext für alle Fenster und Steuerelemente in der Anwendung festgelegt.

### <a name="tlmm-dialogs"></a>TLMM-Dialogfelder
Wenn Sie Fenster auf oberster Ebene, z. B. modale Dialogfelder zu erstellen, ist es wichtig, um sicherzustellen, dass der Thread ist, den richtigen Status aufweist, bevor Sie das HWND erstellt wird. Der Thread kann in versetzt werden System Awareness durch Verwenden der CDpiScope-Hilfsmethode in systemeigenen oder verwaltet das Hilfsobjekt DpiAwareness.EnterDpiScope in. (TLMM sollte im Allgemeinen auf nicht-WPF-Dialoge/Windows verwendet werden.)

### <a name="child-level-mixed-mode-clmm"></a>Untergeordnete Gemischter Modus (CLMM)

Standardmäßig erhalten untergeordnete Fenster im gleichen DPI-Unterstützung Modus als ihren übergeordneten Elementen. Allerdings können Sie SetThreadDpiHostingBehavior um zu überschreiben und wurden untergeordnete Fenster in einem anderen Skalierung Modus als ihre übergeordneten oder Hostbetriebssystem ausgeführt.


#### <a name="clmm-issues"></a>CLMM-Probleme
Die meisten der Aufgaben des UI-Berechnung, die als Teil der wichtigsten messaging-Schleife oder ein Ereignis Kette zufällig müssen bereits in den richtigen DPI-Kontext ausgeführt werden. Aber wenn Koordinate oder größenanpassung Berechnungen außerhalb dieser main Workflows fertig sind, (z. B. während eines Tasks für die Zeit im Leerlauf oder außerhalb des Benutzeroberflächenthreads, klicken Sie dann der aktuelle Kontext der DPI-Wert falsch führt zum Verlust der Benutzeroberfläche oder die falsch größenanpassung Probleme sein kann. Platzieren den Thread in den richtigen Zustand für die Benutzeroberfläche arbeiten in der Regel das Problem behebt.
 
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
```cplusplus
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

**HINWEIS**: Visual Studio unterstützt nur PerMonitorV2-Awareness können, damit der PerMonitor Enum-Wert in der Windows-Wert, der DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 übersetzt.

## <a name="known-issues"></a>Bekannte Probleme

### <a name="windows-forms"></a>Windows Forms

Geändert, um die neuen gemischte Szenarien optimieren, Windows Forms wie erstellt sie Steuerelemente und Fenster ab, wenn ihr übergeordnetes Element nicht explizit festgelegt wurde. Früher verwendet Steuerelemente ohne explizite ein übergeordnetes Element einer internen "" Parken"Fenster" als temporäre übergeordnetes Element an das Steuerelement oder das Fenster erstellt wird. 

"" Parken"Fenster" Ruft die DpiAwarenessContext ab, aus dem Prozess, die, dem die Anwendung ausgeführt wird. Das Steuerelement erbt von der gleichen DpiAwarenessContext wie das Fenster "Parken" und würde dann zur ursprünglichen/erwarteten übergeordneten vom Anwendungsentwickler ordnen.  Dies funktioniert nicht, wenn das vorgesehene übergeordnete Element für das Steuerelement nicht den gleichen DpiAwarenessContext als das Steuerelement erstellt wird.

Ab .NET 4.8 Wenn das übergeordnete Element für das Steuerelement oder das Fenster nicht explizit festgelegt ist Windows Forms fragt für ein "Parken"-Fenster, das die DpiAwarenessContext des Threads entspricht, in dem das Steuerelement oder Fenster erstellen angefordert wird, und verwenden, die als temporäre übergeordnetes Element. Das heißt, wird bei der Erstellung des Steuerelements jetzt mit der gewünschten DpiAwarenessContext erstellt. Das Steuerelement oder das Fenster wird dann zum übergeordneten Element erwartet vom Anwendungsentwickler erneut übergeordnet.
