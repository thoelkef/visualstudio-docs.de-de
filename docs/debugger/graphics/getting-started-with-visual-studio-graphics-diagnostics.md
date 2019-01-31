---
title: Erste Schritte mit der Grafikdiagnose | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 05/26/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38138e1e6997156042be21c769238d03cf4403e8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014223"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Erste Schritte mit Visual Studio-Grafikdiagnose
In diesem Abschnitt bereiten Sie sich auf die erstmalige Verwendung der Grafikdiagnose vor. Anschließend erfassen Sie Frames aus einer Direct3D-App und untersuchen diese in der Grafikanalyse.  
  
## <a name="requirements"></a>Anforderungen  
 Um die Grafikdiagnose in Visual Studio verwenden zu können, müssen Sie Visual Studio Enterprise, Visual Studio Professional oder Visual Studio Community verwenden.  Andere Editionen, einschließlich von Visual Studio Code, enthalten diese Funktion nicht.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Erforderliche Komponenten für Windows 10  
 Die optionale Windows-Funktion *Grafiktools* stellt die Infrastruktur für die Erfassung und Wiedergabe bereit, die für die Grafikdiagnose in Windows 10 erforderlich ist.  
  
 Informationen zum Installieren von Grafiktools finden Sie unter [Installieren von Grafiktools für Windows 10](#InstallGraphicsTools).  
  
##  <a name="InstallGraphicsTools"></a> Installieren von Grafiktools für Windows 10  
 In Windows 10 wird die Infrastruktur für die Grafikdiagnose durch eine optionale Funktion von Windows mit der Bezeichnung *Grafiktools* bereitgestellt. Diese Funktion ist erforderlich, um Grafikinformationen in Windows 10 zu erfassen und wiederzugeben, unabhängig davon, ob die erfasste App eine frühere Windows-Version als Ziel hat oder welche Direct3D-Version verwendet wird. Sie können die Grafiktools-Funktion auch vorab installieren. Andernfalls wird sie bei Bedarf installiert, wenn Sie das erste Mal eine Grafikdiagnosesitzung in Visual Studio starten.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>So installieren Sie Grafiktools für Windows 10  
  
1. Geben Sie in der Suche **Apps und Features** und öffnen Sie dann die **Apps & Features** Einstellungen.
  
2. Auf der rechten Seite des der **Apps & Features** Dialogfeld Wählen Sie **optionale Features verwalten** (unter **Apps & Features**).

   Das Dialogfeld **Optionale Features verwalten** wird angezeigt.
  
3. Wählen Sie im Dialogfeld **Optionale Features verwalten** die Option **Feature hinzufügen** aus. Eine Liste der optionalen Funktionen, die Sie installieren können, wird angezeigt.  
  
4. Wählen Sie in der Liste der Funktionen **Grafiktools** und dann **Installieren** aus.  
  
   Die Funktion „Grafiktools“ wird auch automatisch bei der Installation des Windows 10-SDK installiert.  
  
> [!TIP]
>  Die optionale Grafiktools-Funktion von Windows 10 bietet einfache Funktionen für die Erfassung und Wiedergabe, z. B. das Befehlszeilenerfassungsprogramm **dxcap.exe**, das für Support-, Test- und Diagnoseszenarios auf Computern verwendet werden kann, auf denen Entwicklertools nicht installiert sind. Weitere Informationen finden Sie im Artikel [Command-Line Capture Tool (Befehlszeilenerfassungstool)](command-line-capture-tool.md).  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Erstmaliges Verwenden der Grafikdiagnose  
 Nun, da Sie alles haben, was Sie brauchen, können Sie mit der Verwendung der Grafikdiagnose beginnen. Führen Sie folgende Schritte aus:  
  
### <a name="1---create-a-direct3d-app"></a>1. Erstellen einer Direct3D-App  
 Wenn Sie bereits Ihre eigene Direct3D-app, die Grafikdiagnose mit hervorragenden untersuchen haben! Andernfalls verwenden Sie eine der folgenden:

- Die **DirectX 11-App (Universelles Windows)** oder **DirectX 12-App (Universelles Windows)** -Projektvorlagen für Windows 10.
- [Direct3D 12 UAP-Beispiel](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) für Windows 10.  
  
  Stellen Sie sicher, dass Sie die App erstellen können, bevor Sie fortfahren.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2. Starten einer Grafikdiagnosesitzung  
 Nun können Sie mit Ihrer ersten Grafikdiagnosesitzung beginnen. Wählen Sie in Visual Studio im Hauptmenü **Debuggen, Grafiken, Grafikdebuggen starten**, oder drücken Sie **Alt + F5**. Daraufhin wird Ihre App unter „Grafikdiagnose“ gestartet, und das Fenster für die Diagnosesitzung wird in Visual Studio angezeigt.  
  
> [!IMPORTANT]
>  Wenn Sie Ihre App in Windows 10 ausführen und die optionale Grafiktools-Funktion noch nicht installiert wurde, werden Sie aufgefordert, dies jetzt nachzuholen. Sie müssen diese installieren, bevor Sie die Grafikdiagnose in Windows 10 verwenden können.  
  
### <a name="3---capture-frames"></a>3. Erfassen von Frames  
 Sie können Frames erfassen, sobald die App gestartet wird.  
  
#### <a name="to-capture-single-frames"></a>So erfassen Sie einzelne Frames  
  
-   Wählen Sie in Visual Studio in der Grafik-Symbolleiste oder im Fenster für die Diagnosesitzung die Schaltfläche **Frame erfassen** aus. Oder, wenn Ihre app den Fokus besitzt, drücken Sie einfach die **Druck** auf der Tastatur die Taste.
  
#### <a name="to-capture-a-sequence-of-frames"></a>So erfassen Sie eine Sequenz von Frames  
  
- Legen Sie in Visual Studio im Fenster für die Diagnosesitzung die Option **Zu erfassende Frames** auf die Anzahl der Frames fest, die Sie in einer Sequenz erfassen möchten. Erfassen Sie anschließend die Sequenz mithilfe einer der Methoden, die weiter oben zum Erfassen einzelner Frames beschrieben wurden.  
  
   Legen Sie **Zu erfassende Frames** auf *1* fest, um einzelne Frames erneut zu erfassen.  
  
  Wenn Sie mit dem Erfassen von Frames fertig sind, beenden Sie einfach die App, oder wählen Sie die Schaltfläche **Beenden** in der Grafik-Symbolleiste oder im Fenster für die Diagnosesitzung aus.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4. Untersuchen von erfassten Frames in der Grafikanalyse  
 Sie können nun die Frames überprüfen, die Sie gerade erfasst haben. Um die Analyse eines Frames zu starten, wählen Sie im Fenster für die Diagnosesitzung die Framenummer des Frames aus, den Sie untersuchen möchten. Daraufhin wird der Frame in der **Grafikanalyse** geöffnet, wo Sie die Grafikdiagnosetools verwenden können, um zu untersuchen, inwieweit Ihre App Direct3D verwendet, um Renderingprobleme zu erkennen. Sie können auch das Tool **Frame-Analyse** verwenden, um die Leistung nachzuvollziehen.  
  
 Wenn Sie im Fenster für die Diagnosesitzung den falschen Frame ausgewählt haben oder Sie einen anderen Frame untersuchen möchten, können Sie einen neuen Frame in der Grafikanalyse auswählen. Erweitern Sie auf der Registerkarte **Renderziel** des Grafikprotokollfensters unter dem Renderzielbild die **Frameliste**, und wählen Sie dann einen anderen zu untersuchenden Frame aus.  
  
 Weitere Informationen zur Verwendung der Grafikanalyse-Tools zusammen verwenden, finden Sie unter den [Beispiele](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Direct3D 12-Grafiken](/windows/desktop/direct3d12/direct3d-12-graphics)