---
title: Ersten Einstieg in Grafikdiagnose | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9056fdae9d0eff55c572d8e38503d88269dbde3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704708"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Erste Schritte mit Visual Studio-Grafikdiagnose
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt bereiten Sie sich auf die erstmalige Verwendung der Grafikdiagnose vor. Anschließend erfassen Sie Frames aus einer Direct3D-App und untersuchen diese in der Grafikanalyse.

## <a name="requirements"></a>Anforderungen
 Um die Grafikdiagnose in Visual Studio 2015 zu verwenden, müssen Sie eine dieser Editionen besitzen:

- Visual Studio 2015 Enterprise

- Visual Studio 2015 Professional

- Visual Studio 2015 Community

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Erforderliche Komponenten für Windows 10
 Die optionale Windows-Funktion *Grafiktools* stellt die Infrastruktur für die Erfassung und Wiedergabe bereit, die für die Grafikdiagnose in Windows 10 erforderlich ist.

 Informationen zum Installieren von Grafiktools finden Sie unter [Installieren von Grafiktools für Windows 10](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Erforderliche Komponenten für Windows 8.1
 Das Windows Software Development Kit (SDK) für Windows 8.1 bietet die Infrastruktur für die Erfassung und Wiedergabe, die für die Grafikdiagnose unter Windows 8.1 erforderlich ist, und unterstützt die Entwicklung für Windows 8.1 und Windows 8.

 [Herunterladen des Windows Software Development Kit (SDK) für Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Um einen Remotewiedergabecomputer zu verwenden, der Windows 10 in einem Entwicklungscomputer mit Windows 8.1 ausführt, müssen Sie auf dem Entwicklungscomputer das Windows 10-SDK und auf dem Wiedergabecomputer die optionale Grafiktools-Funktion installieren.

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Installieren von Grafiktools für Windows 10
 In Windows 10 wird die Infrastruktur für die Grafikdiagnose durch eine optionale Funktion von Windows mit der Bezeichnung *Grafiktools* bereitgestellt. Diese Funktion ist erforderlich, um Grafikinformationen in Windows 10 zu erfassen und wiederzugeben, unabhängig davon, ob die erfasste App eine frühere Windows-Version als Ziel hat oder welche Direct3D-Version verwendet wird. Sie können die Grafiktools-Funktion auch vorab installieren. Andernfalls wird sie bei Bedarf installiert, wenn Sie das erste Mal eine Grafikdiagnosesitzung in Visual Studio starten.

#### <a name="to-install-graphics-tools-for-windows-10"></a>So installieren Sie Grafiktools für Windows 10

1. Wählen Sie im **Startmenü** die Option **Einstellungen**aus. Das Dialogfeld **Einstellungen** wird angezeigt.

2. Wählen Sie im Dialogfeld **Einstellungen** die Option **System**aus, und wählen Sie dann in der Liste der System Einstellungen **installierte apps** aus.

3. Wählen Sie auf der rechten Seite des Dialog Felds " **Einstellungen** " die **Option optionale Features verwalten** unter **installierte apps und Features**aus. Das Dialogfeld **Optionale Features verwalten** wird angezeigt.

4. Wählen Sie im Dialogfeld **Optionale Features verwalten** die Option **Feature hinzufügen** aus. Eine Liste der optionalen Funktionen, die Sie installieren können, wird angezeigt.

5. Wählen Sie in der Liste der Funktionen **Grafiktools** und dann **Installieren** aus.

   Die Grafiktools-Funktion wird auch automatisch bei der Installation des Windows 10-SDK installiert.

> [!TIP]
> Die optionale Grafiktools-Funktion von Windows 10 bietet einfache Funktionen für die Erfassung und Wiedergabe, z. B. das Befehlszeilenerfassungsprogramm **dxcap.exe**, das für Support-, Test- und Diagnoseszenarios auf Computern verwendet werden kann, auf denen Entwicklertools nicht installiert sind. Weitere Informationen finden Sie im Artikel [Command-Line Capture Tool (Befehlszeilenerfassungstool)](../debugger/command-line-capture-tool.md).

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Erstmaliges Verwenden der Grafikdiagnose
 Nun, da Sie alles haben, was Sie brauchen, können Sie mit der Verwendung der Grafikdiagnose beginnen. Führen Sie folgende Schritte aus:

### <a name="1---create-a-direct3d-app"></a>1\. Erstellen einer Direct3D-App
 Wenn Sie bereits Ihre eigene Direct3D-App zum Entdecken der Grafikdiagnose haben, ist das eine gute Voraussetzung. Andernfalls können Sie eines der in der Code Gallery verfügbaren Direct3D-Beispiele verwenden.

- Wenn Sie Grafikdiagnose mit Direct3D 12 unter Windows 10 unter Verwendung von Visual Studio 2015 testen möchten, testen Sie das [Direct3D 12 UAP-Beispiel](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) für Windows 10.

- Wenn Sie Grafikdiagnose mit Direct3D 11 unter Windows 10 oder Windows 8.1 ausprobieren möchten, können Sie die Projektvorlagen **DirectX-app (Windows Universal)** oder  **DirectX-app (Windows 8.1)** verwenden. Sie können auch das [DirectX Marble Maze-Spielbeispiel](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) für Windows 8.1 ausprobieren, um etwas interessanteres zu finden.

  Stellen Sie sicher, dass Sie die App erstellen können, bevor Sie fortfahren.

### <a name="2---start-a-graphics-diagnostics-session"></a>2\. Starten einer Grafikdiagnosesitzung
 Nun können Sie mit Ihrer ersten Grafikdiagnosesitzung beginnen. Wählen Sie in Visual Studio im Hauptmenü **Debuggen, Grafiken, Diagnose starten**aus, oder drücken Sie einfach **ALT + F5**. Daraufhin wird Ihre App unter „Grafikdiagnose“ gestartet, und das Fenster für die Diagnosesitzung wird in Visual Studio angezeigt.

> [!IMPORTANT]
> Wenn Sie Ihre App in Windows 10 ausführen und die optionale Grafiktools-Funktion noch nicht installiert wurde, werden Sie aufgefordert, dies jetzt nachzuholen. Sie müssen diese installieren, bevor Sie die Grafikdiagnose in Windows 10 verwenden können.

### <a name="3---capture-frames"></a>3\. Erfassen von Frames
 Sie können Frames erfassen, sobald die App gestartet wird.

##### <a name="to-capture-single-frames"></a>So erfassen Sie einzelne Frames

- Wählen Sie in Visual Studio in der Grafik-Symbolleiste oder im Fenster für die Diagnosesitzung die Schaltfläche **Frame erfassen** aus. Wenn Ihre APP den Fokus hat, drücken Sie einfach den **Bildschirm zum Drucken**.

##### <a name="to-capture-a-sequence-of-frames"></a>So erfassen Sie eine Sequenz von Frames

- Legen Sie in Visual Studio im Fenster für die Diagnosesitzung die Option **Zu erfassende Frames** auf die Anzahl der Frames fest, die Sie in einer Sequenz erfassen möchten. Erfassen Sie anschließend die Sequenz mithilfe einer der Methoden, die weiter oben zum Erfassen einzelner Frames beschrieben wurden.

   Zum erneuten erfassen einzelner Frames legen Sie **Frames** fest, die erfasst werden sollen `1` .

  Wenn Sie mit dem Erfassen von Frames fertig sind, beenden Sie einfach die App, oder wählen Sie die Schaltfläche **Beenden** in der Grafik-Symbolleiste oder im Fenster für die Diagnosesitzung aus.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4. Untersuchen von erfassten Frames in der Grafikanalyse
 Sie können nun die Frames überprüfen, die Sie gerade erfasst haben. Um die Analyse eines Frames zu starten, wählen Sie im Fenster für die Diagnosesitzung die Framenummer des Frames aus, den Sie untersuchen möchten. Daraufhin wird der Frame in der **Grafikanalyse** geöffnet, wo Sie die Grafikdiagnosetools verwenden können, um zu untersuchen, inwieweit Ihre App Direct3D verwendet, um Renderingprobleme zu erkennen. Sie können auch das Tool **Frame-Analyse** verwenden, um die Leistung nachzuvollziehen.

 Wenn Sie im Fenster für die Diagnosesitzung den falschen Frame ausgewählt haben oder Sie einen anderen Frame untersuchen möchten, können Sie einen neuen Frame in der Grafikanalyse auswählen. Erweitern Sie auf der Registerkarte **Renderziel** des Grafikprotokollfensters unter dem Renderzielbild die **Frameliste**, und wählen Sie dann einen anderen zu untersuchenden Frame aus.

 Weitere Informationen zur gemeinsamen Verwendung der Grafikanalyse-Tools finden Sie in den [Beispielen](../debugger/graphics-diagnostics-examples.md).

## <a name="see-also"></a>Weitere Informationen
 [Direct3D 12-Grafiken](https://msdn.microsoft.com/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
