---
title: Erste Schritte mit Visual Studio-Grafikdiagnose | Microsoft Docs
ms.custom: ''
ms.date: 05/26/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2804b07db0b7cf8d01c8578877d4b722d6ceb96
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477520"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Erste Schritte mit Visual Studio-Grafikdiagnose
In diesem Abschnitt bereiten Sie sich auf die erstmalige Verwendung der Grafikdiagnose vor. Anschließend erfassen Sie Frames aus einer Direct3D-App und untersuchen diese in der Grafikanalyse.  
  
## <a name="requirements"></a>Anforderungen  
 Um die Grafikdiagnose in Visual Studio verwenden, müssen Sie Visual Studio Enterprise, Visual Studio Professional oder Visual Studio-Community verwenden.  Andere Editionen, einschließlich Visual Studio-Code, enthalten diese Funktion nicht.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Erforderliche Komponenten für Windows 10  
 Die optionale Windows-Funktion *Grafiktools* bietet die Aufzeichnung und Wiedergabe der Infrastruktur, die für Grafikdiagnose in Windows 10 erforderlich ist.  
  
 Informationen zum Installieren von Grafiktools finden Sie unter [installieren Sie Grafiktools für Windows 10](#InstallGraphicsTools).  
  
##  <a name="InstallGraphicsTools"></a> Installieren von Grafiktools für Windows 10  
 In Windows 10 wird die Infrastruktur für die Grafikdiagnose durch eine optionale Funktion von Windows mit der Bezeichnung bereitgestellt *Grafiktools*. Diese Funktion ist erforderlich, um Grafikinformationen in Windows 10 zu erfassen und wiederzugeben, unabhängig davon, ob die erfasste App eine frühere Windows-Version als Ziel hat oder welche Direct3D-Version verwendet wird. Sie können die Grafiktools-Funktion auch vorab installieren. Andernfalls wird sie bei Bedarf installiert, wenn Sie das erste Mal eine Grafikdiagnosesitzung in Visual Studio starten.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>So installieren Sie Grafiktools für Windows 10  
  
1.  Geben Sie Suche **Apps und Funktionen** und öffnen Sie dann die **Apps & Features** Einstellungen.
  
3.  Auf der rechten Seite von der **Apps & Features** Dialogfeld Wählen Sie **optionale Funktionen verwalten** (unter **Apps & Features**).

    Die **optionale Funktionen verwalten** Dialogfeld wird angezeigt.
  
4.  In der **optionale Funktionen verwalten** Dialogfeld Wählen Sie **Hinzufügen einer Funktion**. Eine Liste der optionalen Funktionen, die Sie installieren können, wird angezeigt.  
  
5.  Wählen Sie **Grafiktools** aus der Liste der Funktionen, und wählen Sie dann **installieren**.  
  
 Die Funktion „Grafiktools“ wird auch automatisch bei der Installation des Windows 10-SDK installiert.  
  
> [!TIP]
>  Die optionale Grafiktools-Funktion von Windows 10 bietet einfache Funktionen für die Erfassung und Wiedergabe, z. B. das Befehlszeilen-erfassungs-Programm **dxcap.exe**–, die verwendet werden kann, in Support-, Test- und diagnoseszenarien auf Computer, auf dem Entwickler-Tools installiert sind. Weitere Informationen finden Sie unter der [Befehlszeilen-Erfassungs-Tool](command-line-capture-tool.md) Thema.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Erstmaliges Verwenden der Grafikdiagnose  
 Nun, da Sie alles haben, was Sie brauchen, können Sie mit der Verwendung der Grafikdiagnose beginnen. Führen Sie folgende Schritte aus:  
  
### <a name="1---create-a-direct3d-app"></a>1. Erstellen einer Direct3D-App  
 Wenn Sie bereits Ihre eigene Direct3D-app zum Entdecken der Grafikdiagnose mit hervorragend haben! Andernfalls verwenden Sie eine der folgenden:

- Die **DirectX 11-App (universelle Windows)** oder **DirectX 12-App (universelle Windows)** -Projektvorlagen für Windows 10.
- [Direct3D 12 UAP-Beispiel](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) für Windows 10.  
  
 Stellen Sie sicher, dass Sie die App erstellen können, bevor Sie fortfahren.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2. Starten einer Grafikdiagnosesitzung  
 Nun können Sie mit Ihrer ersten Grafikdiagnosesitzung beginnen. Wählen Sie in Visual Studio im Hauptmenü **Debuggen, Grafiken, Grafiken Debugging starten**, oder drücken Sie einfach **Alt + F5**. Daraufhin wird Ihre App unter „Grafikdiagnose“ gestartet, und das Fenster für die Diagnosesitzung wird in Visual Studio angezeigt.  
  
> [!IMPORTANT]
>  Wenn Sie Ihre App in Windows 10 ausführen und die optionale Grafiktools-Funktion noch nicht installiert wurde, werden Sie aufgefordert, dies jetzt nachzuholen. Sie müssen diese installieren, bevor Sie die Grafikdiagnose in Windows 10 verwenden können.  
  
### <a name="3---capture-frames"></a>3. Erfassen von Frames  
 Sie können Frames erfassen, sobald die App gestartet wird.  
  
#### <a name="to-capture-single-frames"></a>So erfassen Sie einzelne Frames  
  
-   Wählen Sie in Visual Studio die **Frame erfassen** Schaltfläche aus dem Grafik-Symbolleiste oder die Diagnose Sitzung-Fenster. Oder, wenn Ihre Anwendung den Fokus besitzt, drücken Sie einfach die **Druck** auf der Tastatur die Taste.
  
#### <a name="to-capture-a-sequence-of-frames"></a>So erfassen Sie eine Sequenz von Frames  
  
-   Legen Sie in Visual Studio im Fenster diagnosesitzung **zu erfassende Frames** die Anzahl der Frames, die Sie in einer Sequenz erfassen möchten, klicken Sie dann mit der Sie einzelne Frames erfassen oben beschriebenen Methoden erfassen die Sequenz.  
  
     Um einzelne Frames erneut zu erfassen, legen Sie **zu erfassende Frames** auf *1*.  
  
 Wenn Sie nur Erfassen von Frames fertig sind, die app zu beenden, oder wählen Sie die **beenden** Schaltfläche aus der Grafik-Symbolleiste oder im Fenster diagnosesitzung.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 – Untersuchen von erfassten Frames in der Grafikanalyse  
 Sie können nun die Frames überprüfen, die Sie gerade erfasst haben. Um die Analyse eines Frames zu starten, wählen Sie im Fenster für die Diagnosesitzung die Framenummer des Frames aus, den Sie untersuchen möchten. Daraufhin wird den Frame in der **Grafikanalyse**, können der Grafikdiagnose-Tools untersuchen mithilfe, inwieweit Ihre app Direct3D verwendet, um Renderingprobleme, oder verwenden Sie die **Frame-Analyse** -tool in Verstehen Sie die Leistung.  
  
 Wenn Sie im Fenster für die Diagnosesitzung den falschen Frame ausgewählt haben oder Sie einen anderen Frame untersuchen möchten, können Sie einen neuen Frame in der Grafikanalyse auswählen. Auf der **Renderziel** Erweitern des grafikprotokollfensters unter dem renderzielbild die **Frameliste** und wählen Sie dann auf einen anderen zu untersuchenden Frame.  
  
 Weitere Informationen zum zusammen verwenden, die Grafikanalyse-Tools finden Sie unter der [Beispiele](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Direct3D 12-Grafiken](http://msdn.microsoft.com/en-us/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)