---
title: 'Exemplarische Vorgehensweise: Programm gesteuertes erfassen von Grafik Informationen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2036588fe04825b0fe1a1aa2db7ae8f7e0b5ad4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734767"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Exemplarische Vorgehensweise: Programmgesteuertes Erfassen von Grafikinformationen
Sie können die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Grafikdiagnose zur programmgesteuerten Erfassung von Grafikinformationen aus einer Direct3D-App verwenden.

Programmgesteuerte Erfassung ist in Szenarien wie den folgenden nützlich:

- Beginnen Sie programmgesteuerte Erfassung, wenn Ihre Grafik-App kein vorhandenes Swapchain verwendet, etwa wenn sie auf einer Textur rendert.

- Beginnen Sie programmgesteuerte Erfassung, wenn Ihre Grafik-App überhaupt kein Rendern ausführt, etwa wenn in ihr DirectCompute verwendet wird, um Berechnungen auszuführen.

- Aufruf `CaptureCurrentFrame`when ein Renderingproblem in manuellen Tests schwer zu antizipieren und zu erfassen, kann jedoch Programm gesteuert mithilfe von Informationen über den Status der App zur Laufzeit vorhergesagt werden.

## <a name="CaptureDX11_2"></a> Programmgesteuerte Erfassung in Windows 10
In diesem Teil der exemplarischen Vorgehensweise wird die programmgesteuerte Erfassung in Apps gezeigt, die die DirectX 11.2-API unter Windows 10 verwenden, in der die Methode der stabilen Erfassung verwendet wird.

In diesem Abschnitt wird gezeigt, wie folgende Aufgaben ausgeführt werden:

- Vorbereiten Ihrer App für die Verwendung der programmgesteuerten Erfassung

- Abrufen der Schnittstelle IDXGraphicsAnalysis

- Aufzeichnen von Grafikinformationen

> [!NOTE]
> Vorherige Implementierungen der programmgesteuerten Erfassung stützten sich auf Remotetools für Visual Studio für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], um Erfassungs Funktionen bereitzustellen.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Vorbereiten Ihrer App für die Verwendung der programmgesteuerten Erfassung
Um programmgesteuerte Erfassung in Ihrer App verwenden zu können, muss diese die erforderlichen Header enthalten. Diese Header sind Bestandteile des Windows 10 SDK.

##### <a name="to-include-programmatic-capture-headers"></a>So schließen Sie die Header für die programmgesteuerte Erfassung ein

- Schließen Sie diese Header in die Quelldatei ein, in der Sie die IDXGraphicsAnalysis-Schnittstelle definieren:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Schließen Sie nicht die Headerdatei „vsgcapture.h“ ein – diese unterstützt die programmgesteuerte Erfassung unter Windows 8.0 und früher –, um die programmgesteuerte Erfassung in Ihren Windows 10-Apps auszuführen. Dieser Header ist nicht mit DirectX 11.2 kompatibel. Wenn diese Datei nach dem einschließen des d3d11_2. h-Headers enthalten ist, gibt der Compiler eine Warnung aus. Wenn "vsgcapture. h" vor "d3d11_2. h" enthalten ist, wird die APP nicht gestartet.

    > [!NOTE]
    > Wenn das DirectX SDK vom Juni 2010 auf Ihrem Computer installiert wurde und der Include-Pfad Ihres Projekts `%DXSDK_DIR%includex86`enthält, verschieben Sie diesen Teil an das Ende des Include-Pfads. Gehen Sie beim Bibliothekspfad genauso vor.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Abrufen der Schnittstelle IDXGraphicsAnalysis
Bevor Sie Grafikinformationen von DirectX 11.2 erfassen können, müssen Sie die DXGI-Debugschnittstelle abrufen.

> [!IMPORTANT]
> Wenn Sie die programmgesteuerte Erfassung verwenden, müssen Sie Ihre APP weiterhin unter Grafik Diagnose (ALT + F5 in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) oder unter dem [Befehlszeilen-Erfassungs Tool](command-line-capture-tool.md)ausführen.

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>So rufen Sie die IDXGraphicsAnalysis-Schnittstelle ab

- Verwenden Sie den folgenden Code, um die IDXGraphicsAnalysis-Schnittstelle an die DXGI-Debugschnittstelle anzuschließen.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Achten Sie darauf, dass Sie die von [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) zurückgegebene `HRESULT` überprüfen, um sicherzustellen, dass Sie vor der Verwendung eine gültige Schnittstelle erhalten

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Wenn `DXGIGetDebugInterface1` den Wert `E_NOINTERFACE` zurückgibt (`error: E_NOINTERFACE No such interface supported`), müssen Sie sicherstellen, dass die App unter der Grafikdiagnose (Alt+F5 in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

### <a name="capturing-graphics-information"></a>Aufzeichnen von Grafikinformationen
Wenn Sie nun über eine gültige `IDXGraphicsAnalysis` -Schnittstelle verfügen, können Sie `BeginCapture` und `EndCapture` verwenden, um Grafikinformationen zu erfassen.

##### <a name="to-capture-graphics-information"></a>So erfassen Grafikinformationen

- Verwenden Sie `BeginCapture`, um mit der Erfassung von Grafikinformationen zu beginnen:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Die Erfassung beginnt sofort, wenn `BeginCapture` aufgerufen wird; es wird auf den nächsten Frame gewartet. Die Erfassung stoppt, wenn der aktuelle Frame dargestellt wird oder wenn Sie `EndCapture`aufrufen:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Geben Sie nach dem `EndCapture`-aufzurufen das Grafik Objekt frei.

## <a name="next-steps"></a>Nächste Schritte
In dieser exemplarische Vorgehensweise wurde veranschaulicht, wie Grafikinformationen programmatisch erfasst werden. Im nächsten Schritt haben Sie folgende Möglichkeit:

- Erfahren Sie, wie Sie erfasste Grafikinformationen mithilfe der Grafikdiagnose-Tools analysieren können. Siehe [Übersicht](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erfassen von Grafikinformationen](walkthrough-capturing-graphics-information.md)
- [Capturing Graphics Information](capturing-graphics-information.md)
- [Befehlszeilen-Erfassungstool](command-line-capture-tool.md)
