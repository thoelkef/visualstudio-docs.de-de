---
title: Einstieg in die Grafik Diagnose | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 05/26/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 575b0254768ac359e43cd5b04c23a220549ac973
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557916"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Erste Schritte mit Visual Studio-Grafikdiagnose
In diesem Abschnitt bereiten Sie sich auf die erstmalige Verwendung der Grafikdiagnose vor. Anschließend erfassen Sie Frames aus einer Direct3D-App und untersuchen diese in der Grafikanalyse.

## <a name="requirements"></a>Requirements (Anforderungen)
 Um Grafikdiagnose in Visual Studio verwenden zu können, müssen Sie Visual Studio Enterprise, Visual Studio Professional oder Visual Studio Community verwenden.  Diese Funktion ist in anderen Editionen, einschließlich Visual Studio Code, nicht enthalten.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Voraussetzungen für Windows 10
 Die optionale Windows-Funktion *Grafiktools* stellt die Infrastruktur für die Erfassung und Wiedergabe bereit, die für die Grafikdiagnose in Windows 10 erforderlich ist.

 Informationen zum Installieren von Grafiktools finden Sie unter [Installieren von Grafiktools für Windows 10](#InstallGraphicsTools).

## <a name="InstallGraphicsTools"></a> Installieren von Grafiktools für Windows 10
 In Windows 10 wird die Infrastruktur für die Grafikdiagnose durch eine optionale Funktion von Windows mit der Bezeichnung *Grafiktools* bereitgestellt. Diese Funktion ist erforderlich, um Grafikinformationen in Windows 10 zu erfassen und wiederzugeben, unabhängig davon, ob die erfasste App eine frühere Windows-Version als Ziel hat oder welche Direct3D-Version verwendet wird. Sie können die Grafiktools-Funktion auch vorab installieren. Andernfalls wird sie bei Bedarf installiert, wenn Sie das erste Mal eine Grafikdiagnosesitzung in Visual Studio starten.

#### <a name="to-install-graphics-tools-for-windows-10"></a>So installieren Sie Grafiktools für Windows 10

1. Geben Sie im Suchfeld **apps und Features** ein, und öffnen Sie dann die Einstellungen für **Apps & Features** .

2. Wählen Sie auf der rechten Seite der Einstellungen für **Apps & Features** die **Option optionale Features** (unter **Apps & Features**) aus.

   Die **optionalen Funktions** Einstellungen werden angezeigt.

3. Wählen Sie in den **optionalen Funktions** Einstellungen die Option **Feature hinzufügen**aus. Eine Liste der optionalen Funktionen, die Sie installieren können, wird angezeigt.

4. Wählen Sie in der Liste der Funktionen **Grafiktools** und dann **Installieren** aus.

   Die Grafiktools-Funktion wird auch automatisch bei der Installation des Windows 10-SDK installiert.

> [!TIP]
> Die optionale Grafiktools-Funktion von Windows 10 bietet einfache Funktionen für die Erfassung und Wiedergabe, z. B. das Befehlszeilenerfassungsprogramm **dxcap.exe**, das für Support-, Test- und Diagnoseszenarios auf Computern verwendet werden kann, auf denen Entwicklertools nicht installiert sind. Weitere Informationen finden Sie im Artikel [Command-Line Capture Tool (Befehlszeilenerfassungstool)](command-line-capture-tool.md).

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Erstmaliges Verwenden der Grafikdiagnose
 Nun, da Sie alles haben, was Sie brauchen, können Sie mit der Verwendung der Grafikdiagnose beginnen. Führen Sie einfach die folgenden Schritte aus:

### <a name="1---create-a-direct3d-app"></a>1\. Erstellen einer Direct3D-App
 Wenn Sie bereits über eine eigene Direct3D-App verfügen, mit der Sie Grafikdiagnose erkunden können, ist das gut! Verwenden Sie andernfalls eine der folgenden Aktionen:

- Die **DirectX 11-app (universelle Windows)** oder DirectX 12-APP-Projektvorlagen **(universelle Windows** -APP) für Windows 10.
- [Direct3D 12 UAP-Beispiel](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) für Windows 10.

  Stellen Sie sicher, dass Sie die App erstellen können, bevor Sie fortfahren.

### <a name="2---start-a-graphics-diagnostics-session"></a>2\. Starten einer Grafikdiagnosesitzung
 Nun können Sie mit Ihrer ersten Grafikdiagnosesitzung beginnen. Wählen Sie in Visual Studio im Hauptmenü **Debuggen, Grafiken, Grafik Debugging starten**aus, oder drücken Sie einfach **ALT + F5**. Daraufhin wird Ihre App unter „Grafikdiagnose“ gestartet, und das Fenster für die Diagnosesitzung wird in Visual Studio angezeigt.

> [!IMPORTANT]
> Wenn Sie Ihre App in Windows 10 ausführen und die optionale Grafiktools-Funktion noch nicht installiert wurde, werden Sie aufgefordert, dies jetzt nachzuholen. Sie müssen diese installieren, bevor Sie die Grafikdiagnose in Windows 10 verwenden können.

### <a name="3---capture-frames"></a>3\. Erfassen von Frames
 Sie können Frames erfassen, sobald die App gestartet wird.

#### <a name="to-capture-single-frames"></a>So erfassen Sie einzelne Frames

- Wählen Sie in Visual Studio in der Grafik-Symbolleiste oder im Fenster für die Diagnosesitzung die Schaltfläche **Frame erfassen** aus. Wenn Ihre APP den Fokus hat, drücken Sie einfach die **druckbildschirm** Taste auf der Tastatur.

#### <a name="to-capture-a-sequence-of-frames"></a>So erfassen Sie eine Sequenz von Frames

- Legen Sie in Visual Studio im Fenster für die Diagnosesitzung die Option **Zu erfassende Frames** auf die Anzahl der Frames fest, die Sie in einer Sequenz erfassen möchten. Erfassen Sie anschließend die Sequenz mithilfe einer der Methoden, die weiter oben zum Erfassen einzelner Frames beschrieben wurden.

   Legen Sie **Zu erfassende Frames** auf *1* fest, um einzelne Frames erneut zu erfassen.

  Wenn Sie mit dem Erfassen von Frames fertig sind, beenden Sie einfach die App, oder wählen Sie die Schaltfläche **Beenden** in der Grafik-Symbolleiste oder im Fenster für die Diagnosesitzung aus.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4\. Untersuchen von erfassten Frames in der Grafikanalyse
 Sie können nun die Frames überprüfen, die Sie gerade erfasst haben. Um die Analyse eines Frames zu starten, wählen Sie im Fenster für die Diagnosesitzung die Framenummer des Frames aus, den Sie untersuchen möchten. Daraufhin wird der Frame in der **Grafikanalyse** geöffnet, wo Sie die Grafikdiagnosetools verwenden können, um zu untersuchen, inwieweit Ihre App Direct3D verwendet, um Renderingprobleme zu erkennen. Sie können auch das Tool **Frame-Analyse** verwenden, um die Leistung nachzuvollziehen.

 Wenn Sie im Fenster für die Diagnosesitzung den falschen Frame ausgewählt haben oder Sie einen anderen Frame untersuchen möchten, können Sie einen neuen Frame in der Grafikanalyse auswählen. Erweitern Sie auf der Registerkarte **Renderziel** des Grafikprotokollfensters unter dem Renderzielbild die **Frameliste**, und wählen Sie dann einen anderen zu untersuchenden Frame aus.

 Weitere Informationen zur gemeinsamen Verwendung der grafikanalyse Tools finden Sie in den [Beispielen](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Weitere Informationen
- [Direct3D 12-Grafiken](/windows/desktop/direct3d12/direct3d-12-graphics)